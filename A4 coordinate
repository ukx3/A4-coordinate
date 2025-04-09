import streamlit as st
from reportlab.lib.pagesizes import A4
from reportlab.pdfgen import canvas
import io

st.set_page_config(page_title="A4 Coordinate Grid Generator")
st.title("📐 A4 Coordinate Grid Generator")
st.markdown("Generate an A4-sized PDF with grid lines and labeled coordinates for layout testing.")

spacing = st.selectbox("Grid spacing (points)", [10, 20, 25, 50, 100], index=1)

if st.button("Generate PDF"):
    buffer = io.BytesIO()
    c = canvas.Canvas(buffer, pagesize=A4)
    width, height = A4

    # Draw vertical lines and label X coordinates
    for x in range(0, int(width), spacing):
        c.setStrokeColorRGB(0.85, 0.85, 0.85)
        c.line(x, 0, x, height)
        c.setFillColorRGB(0, 0, 0)
        c.setFont("Helvetica", 6)
        c.drawString(x + 1, 2, str(x))

    # Draw horizontal lines and label Y coordinates
    for y in range(0, int(height), spacing):
        c.setStrokeColorRGB(0.85, 0.85, 0.85)
        c.line(0, y, width, y)
        c.setFillColorRGB(0, 0, 0)
        c.setFont("Helvetica", 6)
        c.drawString(2, y + 1, str(y))

    c.save()
    buffer.seek(0)

    st.success("✅ PDF generated successfully!")
    st.download_button("📥 Download A4 Grid PDF", buffer, file_name="A4_coordinate_grid.pdf", mime="application/pdf")

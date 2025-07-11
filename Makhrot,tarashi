import streamlit as st
import math

st.set_page_config(page_title="محاسبه مخروط تراشی", layout="centered")

st.title("🔧 محاسبه زاویه و ابعاد مخروط تراشی")
st.markdown("برای محاسبه، سه مقدار را وارد کنید، مقدار چهارم محاسبه می‌شود.")

col1, col2 = st.columns(2)

with col1:
    D = st.text_input("قطر بزرگ (D) بر حسب mm")
    d = st.text_input("قطر کوچک (d) بر حسب mm")

with col2:
    L = st.text_input("طول مخروط (L) بر حسب mm")
    alpha_half_deg = st.text_input("زاویه ساپورت (α/2) بر حسب درجه")

# تبدیل ورودی‌ها
D = float(D) if D else None
d = float(d) if d else None
L = float(L) if L else None
alpha_half_deg = float(alpha_half_deg) if alpha_half_deg else None

# محاسبه
if st.button("🔍 محاسبه"):
    try:
        if alpha_half_deg is None and None not in (D, d, L):
            tan_val = (D - d) / (2 * L)
            alpha_half_rad = math.atan(tan_val)
            alpha_half_deg = math.degrees(alpha_half_rad)
            st.success(f"✅ زاویه ساپورت: {alpha_half_deg:.2f} درجه")

        elif L is None and None not in (D, d, alpha_half_deg):
            alpha_half_rad = math.radians(alpha_half_deg)
            L = (D - d) / (2 * math.tan(alpha_half_rad))
            st.success(f"✅ طول مخروط: {L:.2f} mm")

        elif D is None and None not in (d, L, alpha_half_deg):
            alpha_half_rad = math.radians(alpha_half_deg)
            D = d + 2 * L * math.tan(alpha_half_rad)
            st.success(f"✅ قطر بزرگ: {D:.2f} mm")

        elif d is None and None not in (D, L, alpha_half_deg):
            alpha_half_rad = math.radians(alpha_half_deg)
            d = D - 2 * L * math.tan(alpha_half_rad)
            st.success(f"✅ قطر کوچک: {d:.2f} mm")

        else:
            st.warning("⚠️ لطفاً دقیقاً سه مقدار وارد کنید.")
    except Exception as e:
        st.error(f"❌ خطا در محاسبه: {e}")

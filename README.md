# energy-floo
import streamlit as st
import numpy as np
import matplotlib.pyplot as plt

# Title
st.title("Energy from Sound and Pressure")

# Input values
pressure = st.slider('Pressure (Pa)', min_value=0, max_value=10000, value=5000, step=100)
sound_level = st.slider('Sound Level (dB)', min_value=0, max_value=150, value=60, step=1)
time = st.slider('Time (seconds)', min_value=1, max_value=300, value=30, step=1)

# Simple energy calculation (مثال افتراضي)
# الفكرة هنا هي دمج القيم الثلاثة للحصول على الطاقة (بالواط ساعة أو ميلي جول)
energy = (pressure * sound_level * time) / 100000  # مثال تقريبي لحساب الطاقة

# عرض الطاقة الناتجة
st.write(f"Energy Produced: {energy:.2f} Watt-hours")

# Plotting a simple graph
time_array = np.arange(1, time+1)
energy_array = (pressure * sound_level * time_array) / 100000  # Calculate energy over time

plt.plot(time_array, energy_array, label="Energy over Time")
plt.xlabel('Time (seconds)')
plt.ylabel('Energy (Wh)')
plt.title('Energy vs Time')
plt.legend()
st.pyplot(plt)

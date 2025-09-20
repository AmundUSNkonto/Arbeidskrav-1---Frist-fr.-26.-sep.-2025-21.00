import matplotlib.pyplot as plt

antall_km = 10000

#Forsikring
forsikring_elbil = 5000
forsikring_bensinbil = 7500

trafikkforsikringsavgift = 8.38*365

#Drivstoff
drivstoffforbruk_el = 0.2
drivstoffforbruk_bensin = 1
strømpris = 2

#Bompenger
bom_el = 0.1
bom_bensin = 0.3

#Totalkostnad for året

total_el = forsikring_elbil+trafikkforsikringsavgift+drivstoffforbruk_el*antall_km*strømpris+bom_el*antall_km
total_bensin = forsikring_bensinbil+trafikkforsikringsavgift+drivstoffforbruk_bensin*antall_km+bom_bensin*antall_km
årlig_kostnadsdifferanse = total_bensin-total_el
print(total_bensin)
print(total_el)
print(årlig_kostnadsdifferanse)

# Ønsker å visualisere disse dataene i et stolpediagram
categories = ['Elbil', 'Bensinbil', 'Differanse']
values = [total_el, total_bensin, årlig_kostnadsdifferanse]

# Lage stolpediagram
bars = plt.bar(categories, values)

# Add labels on bars
for bar in bars:
    height = bar.get_height()
    plt.text(bar.get_x() + bar.get_width() / 2, height,
             f'{height:,.0f}kr',  # formats as integer with thousands separator
             ha='center', va='bottom')

# titler
plt.xlabel('Type bil')
plt.ylabel('Kostad (NOK)')
plt.title('Årlig totalkostnad elbil vs bensinbil')

# Show chart
plt.show()

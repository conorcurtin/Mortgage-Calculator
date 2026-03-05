```python
print("This is a Python script")

#Calculating mortgage repayments, interest, the impact of monthly overpayments, and the total money saved over time.


PV = 100000          # Loan amount
r = 0.04/12         # Monthly interest rate (0.040 / 12 = 0.0033)
year = 25
n = year*12            # Number of payments (months)

# Baseline (no overpayment)
pmt = r * PV / (1 - (1+r)**(-n)) # Monthly payment formula that fully repays the loan (principal + interest) over n months
total_paid = pmt * n
total_interest = total_paid - PV

print(f"  Monthly payment: £{pmt:,.0f}")
print(f"  Total paid over {year} years: £{total_paid:,.0f}")
print(f"  Total interest paid: £{total_interest:,.0f}")
print()

# Interest Only
Interest = PV *r
print(f"  Interest only re=payment £{Interest:,.0f}")
print()

# Overpayment
OP = 200.0
pmt_over = pmt + OP  # overpayment increases the monthly payment

# New term with higher payment:
import math
n_over = -math.log(1 - r * PV / pmt_over) / math.log(1 + r)

total_paid_over = pmt_over * n_over
total_interest_over = total_paid_over - PV

months_saved = n - n_over
years_saved = months_saved / 12
interest_savings = total_interest - total_interest_over

print(f"  With £{OP:,.0f} a month overpayment:")
print(f"  New monthly payment: £{pmt_over:,.0f}")
print(f"  New years: {n_over/12:.2f} years")
print(f"  Time saved: {years_saved:.2f} years")
print(f"  Total paid: £{total_paid_over:,.0f}")
print(f"  Total interest: £{total_interest_over:,.0f}")
print(f"  Interest savings vs baseline: £{interest_savings:,.0f}")

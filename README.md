import pandas as pr
dta=pr.DataFrame(columns=['Name','Weight','Height','BMI','Status'])
while True:
    a=input("Enter your name:")
    b=float(input("Enter your Weight in (kg.):"))
    c=float(input("Enter your height ini (meter):"))
    bi=b/(c**2)
    if bi<18.5:
        st=("under weight")
    elif bi<24.9:
        st=("normal")
    elif bi<29.9:
        st=("over weight")
    else:
        st=("obese")
    dt=pr.DataFrame({'Name':[a],'Weight':[b],'Height':[c],'BMI':[round(bi,3)],'Status':[st]})
    if dta.empty:
        dta=dt
    else:
        dta=pr.concat([dta,dt],ignore_index=True)
    d=input("Do you want to add another record..?(yes/no):")
    if d.lower()!='yes':
        break
    print("---BMI Record---")
    print(dta)
    dta.to_csv("bmi_recd.csv",index=False)
    print(" All records saved...")

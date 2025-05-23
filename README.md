import smtplib
import time
import os

os.system("color 4")  

print("=" * 50)
print("                EMAIL SPAMMER")
print("                By zak")
print("=" * 50)

email = input("Ton adresse Gmail: ")
password = input("Mot de passe: ")
to = input("Envoyer à: ")
subject = input("Sujet: ")
message = input("Message: ")
times = int(input("Combien de fois tu veux envoyer: "))

try:
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.starttls()
    server.login(email, password)

    full_msg = f"Subject: {subject}\n\n{message}"

    print("\n[+] Envoi en cours...\n")
    for i in range(times):
        server.sendmail(email, to, full_msg)
        print(f"[{i+1}] Message envoyé")
        time.sleep(1)

    print("\n[✓] Tous les messages ont été envoyés !")
    server.quit()

except Exception as e:
    print("\n[!] Une erreur est survenue:", e)

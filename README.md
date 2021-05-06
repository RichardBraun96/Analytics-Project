# Analytics-Project
import pandas as pd
import openpyxl


einlesen = openpyxl.load_workbook("/Users/sebastianpink/Desktop/Test.xlsx")
tab1 = einlesen['Test']


    def hauptmenu():
        ExcelRead = pd.read_excel("/Users/sebastianpink/Desktop/Test.xlsx")
        print("\n")
        print("Willkommen im Hauptmenu.")
        print("Bitte wählen Sie eine Option aus.")
        print("\n")
        print( "1. Daten anzeigen")
        print("2. Daten ändern")
        print("3. Statistik anzeigen")
        print("\n")
        choice = int(input("Zahl für Option eingeben:"))

        if choice == 1:
            print("\n")
            print(ExcelRead)
            print("\n \n")
            hauptmenu()

        if choice == 2:
            datenaendern()


        if choice == 3:

            statistikmenu()

    def statistikmenu():
        ExcelRead = pd.read_excel("/Users/sebastianpink/Desktop/Test.xlsx")
        print("\n")
        print("1. Alle Statistiken anzeigen")
        print("2. Standardabweichung berechnen")
        print("3. Maximum anzeigen")
        print("4. Minimum anzeigen")
        print("5. Mittelwert anzeigen")
        print("6. Zurück zum Hauptmenu")
        print("\n")
        choice = int(input("Zahl für Option eingeben:"))

        if choice == 1:
            print("\n")
            abweichung = ExcelRead["Temperatur"].std()
            print("Die Standardabweichnung beträgt: %.2f" % abweichung)
            print("Das Maximum ist: ", ExcelRead["Temperatur"].max())
            print("Das Minimum ist: ", ExcelRead["Temperatur"].min())
            print("Der Mittelwert: ", ExcelRead["Temperatur"].mean())
            print("\n")
            statistikmenu()

        if choice == 2:
            print("\n")
            abweichung = ExcelRead["Temperatur"].std()
            print("Die Standardabweichnung beträgt: %.2f" % abweichung )
            print("\n")
            statistikmenu()

        if choice == 3:
            print("\n")
            print("Das Maximum ist: ", ExcelRead["Temperatur"].max())
            print("\n")
            statistikmenu()

        if choice == 4:
            print("\n")
            print("Das Minimum ist: ", ExcelRead["Temperatur"].min())
            print("\n")
            statistikmenu()

        if choice == 5:
            print("\n")
            mittel = ExcelRead["Temperatur"].mean()
            print("Der Mittelwert: %.2f" % mittel)
            print("\n")
            statistikmenu()


        if choice == 6:
            hauptmenu()

    def datenaendern():
        ExcelRead = pd.read_excel("/Users/sebastianpink/Desktop/Test.xlsx")
        print("\n")
        print("1. Letzen Eintrag löschen")
        print("2. Neuen Eintrag hinzufügen")
        print("3. Bestimmten Wert löschen")
        print("4. zurück zum Hauptmenu")
        print("\n")
        choice = int(input("Zahl für Option eingeben:"))

        if choice == 1:
            print("\n")
            rowmax = tab1.max_row
            tab1.delete_rows(rowmax)
            einlesen.save("/Users/sebastianpink/Desktop/Test.xlsx")
            print("Der letzte Eintrag wurde gelöscht")
            print("\n")
            statistikmenu()

        if choice == 2:
            rowmax = tab1.max_row+1
            print("\n")
            neuetemp = float(input("Neue Temperatur eingeben:"))
            tab1.cell(row=rowmax, column=1, value=neuetemp)
            einlesen.save("/Users/sebastianpink/Desktop/Test.xlsx")
            print("Neuer Eintrag wurde hinzugefügt")
            print("\n")
            statistikmenu()

        if choice == 3:
            print("\n")
            zeile = int(input("Welche Zeile soll gelöscht werden?:"))
            richtigzeile = zeile+2
            tab1.delete_rows(richtigzeile)
            einlesen.save("/Users/sebastianpink/Desktop/Test.xlsx")
            print("\n")
            statistikmenu()

        if choice == 4:
            hauptmenu()





    hauptmenu()

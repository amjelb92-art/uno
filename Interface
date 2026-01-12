import tkinter as tk
from tkinter import messagebox

class InterfaceUNO:
    def __init__(self, cartes_jouables_func, jouer_carte_func):
        self.cartes_jouables = cartes_jouables_func
        self.jouer_carte = jouer_carte_func

        self.fenetre = tk.Tk()
        self.fenetre.title("UNO")

        self.label = tk.Label(self.fenetre, text="Cartes jouables :")
        self.label.pack(pady=5)

        self.liste_cartes = tk.Listbox(self.fenetre, width=30)
        self.liste_cartes.pack(pady=5)

        self.bouton = tk.Button(
            self.fenetre,
            text="Jouer la carte",
            command=self.jouer
        )
        self.bouton.pack(pady=10)

        self.rafraichir()

        self.fenetre.mainloop()

    def rafraichir(self):
        self.liste_cartes.delete(0, tk.END)
        for carte in self.cartes_jouables():
            self.liste_cartes.insert(tk.END, carte)

    def jouer(self):
        selection = self.liste_cartes.curselection()
        if not selection:
            messagebox.showwarning("Erreur", "Aucune carte sélectionnée")
            return

        carte = self.liste_cartes.get(selection[0])
        succes = self.jouer_carte(carte)

        if succes:
            self.rafraichir()
        else:
            messagebox.showerror("Erreur", "Carte non jouable")

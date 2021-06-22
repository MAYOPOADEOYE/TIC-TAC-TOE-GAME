# TIC-TAC-TOE-GAME
#Allows a winner to be determined in a criss-cross game


from tkinter import *
def callback(r,c):
	global player
	if player =="X" and type[r][c]==0 and stop_game==False:
		b[r][c].configure(text="X",fg="blue",bg="white")
		type[r][c]="X"
		player="O"

	if player=="O" and type[r][c]==0 and stop_game==False:
		b[r][c].configure(text="O",fg="green",bg="blue")
		type[r][c]="O"
		player="X"

#check_for_winner()  
def check_for_winner():
	global stop_game
	for i in range(3):
		if type[i][0]==type[i][1]==type[i][2]!=0:
			b[i][0].configure(bg="grey")
			b[i][1].configure(bg="grey")
			b[i][2].configure(bg="grey")
			stop_game=True

	for i in range(3):
		if type[0][i]==type[1][i]==type[2][i]!=0:
			b[0][i].configure(bg="grey")
			b[1][i].configure(bg="grey")
			b[2][i].configure(bg="grey")
			stop_game=True

	if type[0][0]==type[1][1]==type[2][2]!=0:
			b[0][0].configure(bg="grey")
			b[1][1].configure(bg="grey")
			b[2][2].configure(bg="grey")

	if type[2][0]==type[1][1]==type[0][2]!=0:
			b[2][0].configure(bg="grey")
			b[1][1].configure(bg="grey")
			b[0][2].configure(bg="grey")
root=Tk()
root.title("GAME")  
root.configure(bg="powder blue")
root.resizable(0,0)
root.geometry("535x600+200+100")



#reset_button
reset_btn=Button(root,text="RESET",font=("Verdana",15,"bold"),height=2,width=20,bg="gainsboro",command=reset)
reset_btn.place(x=120,y=300)

type=[[0,0,0],
	  [0,0,0],
	  [0,0,0]]

b=[[0,0,0],
   [0,0,0],
   [0,0,0]]

for i in range(3):
	for j in range(3):
		b[i][j]=Button(font=("Verdana,60"),width=19,height=2,bg="red",command=lambda r=i,c=j:callback(r,c))
		b[i][j].grid(row=i,column=j)
player="X"
stop_game=False

mainloop()

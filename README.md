# YouTube-Downloader-GUI
import customtkinter
from pytube import YouTube
from tkinter import messagebox
def download_video():
    link=url.get()
    if link =="":
        messagebox.showwarning(title="Invalid link", message="Input a YouTube link \nTry again")
    else:
        yt=YouTube(link)
        try:
            downloaded_video=yt.streams.get_highest_resolution()
            downloaded_video.download("D:/downloade by pytube")
            title=yt.title()
            views=yt.views
            messagebox.showinfo(title="Downloaded", message=f"Download complete\nThe title is {title}\nnumber of views={views}")
        except:
            messagebox.showwarning("FAILED", message=f"Failed to download\nPlease try again and check the connections")
def download_audio():
    link=url.get()
    if link =="":
        messagebox.showwarning(title="Invalid link", message="Input a YouTube link\nTry again")
    else:
        yt=YouTube(link)
        try:
            downloaded_video=yt('mp3')
            downloaded_video.download("D:/downloade by pytube")
            title=yt.title()
            views=yt.views
            messagebox.showinfo(title="Downloaded", message=f"Download complete\nThe title is{title}\nnumber of views={views}")
        except:
            messagebox.showwarning("FAILED", message=f"Failed to download\nPlease try again and check the connections")            
youtube_app=customtkinter.CTk()
youtube_app.title("YouTube Downloader")
youtube_app.geometry("400x200")
youtube_app.resizable(False,False)
customtkinter.set_appearance_mode("dark")
customtkinter.set_default_color_theme("green")
url=customtkinter.CTkEntry(master=youtube_app, width=350, placeholder_text="Enter the link here", placeholder_text_color="white")
url.pack(padx=10,pady=10)
download_button=customtkinter.CTkButton(master=youtube_app, text="Download Audio", text_color="black", command=download_audio)
download_button.pack(padx=10,pady=10)
download_button=customtkinter.CTkButton(master=youtube_app, text="Download Video", text_color="black", command=download_video)
download_button.pack(padx=10,pady=10)
youtube_app.mainloop()

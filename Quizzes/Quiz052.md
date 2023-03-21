# Quiz 52
<img width="914" alt="Screen Shot 2023-03-21 at 12 21 03 PM" src="https://user-images.githubusercontent.com/111751273/226516505-db7de18d-87b6-4497-99e9-ecfe401de27a.png">


## Code
```.py
class MovieDownloader:
    def __init__(self, download_speed):
        if download_speed <= 0:
            raise ValueError("Download speed must be greater than 0")
        self.download_speed = download_speed

    def calculate_download_time(self, movie_size):
        if movie_size <= 0:
            raise ValueError("Movie size must be greater than 0")
        download_time_seconds = movie_size / (self.download_speed * 1024 * 1024)
        minutes, seconds = divmod(download_time_seconds, 60)
        return f"{int(minutes)} minutes {int(seconds)} seconds"
```


## Proof
<img width="1512" alt="Screen Shot 2023-03-21 at 12 21 19 PM" src="https://user-images.githubusercontent.com/111751273/226516532-4ed08f90-32c7-4062-95f4-eac7a74fcaa3.png">

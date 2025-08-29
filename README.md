# Code-Blocks-Experiment-1
Implementation of Go-Back-N Protocol – Sliding Window

🎯 Aim

To write and execute a program for the Go-Back-N protocol using the sliding window technique.

🛠️ Equipments Required

• 	Personal Computer

• 	Turbo C Compiler

📋 Procedure
1. 	Connect two computers in a Wired/Wireless LAN.
2. 	Ensure both machines are on the same network and can ping each other.
3. 	Open a new C file in Code::Blocks or any C IDE and type the program.
4. 	Navigate to:
Project -> Properties -> Project Build Options -> Linker Settings
Add: netproto and pthread
5. 	Execute the program on both server and client machines.
6. 	Enter:
• 	IP address of the remote machine
• 	Port address of both local and remote machines
• 	Error rate
7. 	Choose the file and verify the Go-Back-N protocol operation.

💻 Program
```
#include <stdio.h>
#include <string.h>
#define WINDOW_SIZE 4
#define MAX_FRAMES 100
#define FRAME_LEN  20
int main() {
    int n, i, ack;
    int window_start = 1;
    char frame[MAX_FRAMES + 1][FRAME_LEN];
    printf("SLIDING WINDOW PROTOCOL\n");
    printf("Enter the number of frames to send (max %d): ", MAX_FRAMES);
    if (scanf("%d", &n) != 1) return 0;
    if (n < 1 || n > MAX_FRAMES) {
        printf("Invalid number of frames.\n");
        return 0;
    }
    for (i = 1; i <= n; i++) {
        printf("Content for frame %d: ", i);
        scanf("%19s", frame[i]);
    }
    while (window_start <= n) {
        printf("\nSending frames: ");
        for (i = window_start; i < window_start + WINDOW_SIZE && i <= n; i++) {
            printf("Frame %d ", i);
        }
        printf("\nEnter frame number with no ACK (or 0 for all ACK): ");
        if (scanf("%d", &ack) != 1) break;

        if (ack == 0) {
            printf("All frames acknowledged. Moving window forward.\n");
            window_start += WINDOW_SIZE;
        } else if (ack >= window_start && ack <= n) {
            printf("No acknowledgement for frame %d.\n", ack);
            printf("Resending frames starting from frame %d:\n", ack);
            window_start = ack;  // go back to that frame
        } else {
            printf("Invalid ACK number. Try again.\n");
        }
    }

    printf("\nAll frames sent successfully.\n");
    return 0;
}
```

🖥️ Sample Output
<img width="1210" height="984" alt="code block 1" src="https://github.com/user-attachments/assets/e8e4b6d8-7bb3-454e-8e02-6349c08a432a" />

✅ Result

Thus, the Go-Back-N protocol using the sliding window technique was successfully implemented and verified.

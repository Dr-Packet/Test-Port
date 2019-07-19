import socket
import time
import csv





retry = 3
delay = 10
timeout = 3



def isOpen(ip, port):
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(timeout)

        try:
                s.connect((ip, int(port)))
                s.shutdown(socket.SHUT_RDWR)
                return True
        except:
                return False
        finally:
                s.close()

def checkHost(ip, port):
        ipup = False
        for i in range(retry):

                if isOpen(ip, port):
                        ipup = True
                        print (ip + " ", port + ' - UP')
                        break
                else:
                        if i < retry-1:
                            time.sleep(delay)
                        else:
                           print (ip + " ", port + ' - DOWN') 
                            
                            
                        
        return ipup



with open('Ports.txt') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    line_count = 0
    for row in csv_reader:
        ip = row[0]
        port = row[1]
        checkHost (ip, port)
        line_count += 1

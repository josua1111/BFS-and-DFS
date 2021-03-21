Tugas Sistem Pakar
Nama : Josuansef Pardede
NPM : 1184091
Kelas : D4 TI 3A

# Aplikasi Sistem Pakar Depth First Search dan Breadth First Search

Pemahaman
Depth First Search (DFS) adalah salah satu algoritma penelusuran struktur graf atau pohon berdasarkan kedalaman. Node ditelusuri dari root kemudian ke salah satu node anaknya (bawahnya) misalnya prioritas penelusuran berdasarkan anak pertama (Node sebelah kiri), maka penelusuran dilakukan terus melalui node anak pertama dari node anak pertama level sebelumnya hingga mencapai level terdalam atau lebih bawah. Setelah sampai di level terdalam, penelusuran akan kembali ke 1 level sebelumnya untuk menelusuri node anak kedua pada pohon biner (node sebelah kanan) lalu kembali ke langkah sebelumnya dengan menelusuri node anak pertama lagi sampai level terdalam dan seterusnya.
Penjelasan DepthFirstSearch.py
Peta dibuat yaitu dengan parameter A,B,C,D,F,G,H,I,J,K,L
Selanjutnya dibuat fungsi definisi kelas dfs dengan parameter graph, mulai, goal yaitu simulasi dari awal (graph) sampai selesai (goal)
Lalu dibuat pengandaian yaitu pada DFS, jalur graph/ awal adalah tujuan sedangkan goal adalah permulaan
peta = {'A':set(['B']),
        'B':set(['C','A']),
        'C':set(['H','B','I','D']),
        'D':set(['C','E','H','F']),
        'E':set(['D']),
        'F':set(['D','G']),
        'G':set(['F','H']),
        'H':set(['L','C','G','D']),
        'I':set(['C','J','K']),
        'J':set(['I']),
        'K':set(['L','I']),
        'L':set(['K','H'])}
        
def dfs(graph, mulai, goal):
(# mengecek semua node)
    explored = []
(# mengecek semua jalur)
    stack = [[mulai]]
    
(# kembali ke jalur apabila awal adalah tujuan)
    if mulai == goal:
        return "Awal adalah Tujuan"

(# perulangan sampai dengan semua jalur telah diperiksa)
    while stack:
        (# masukkan antrian paling belakang ke variabel jalur)
        jalur = stack.pop(-1)
        (# ambil node terakhir dari jalur)
        node = jalur[-1]
        ( # jika node tidak sama dengan tujuan, maka cek apakah node tidak ada di explored)
        if node not in explored:
            neighbours = graph[node]
            (# Memasukan semua isi graph node kedalam neighbours)
            (# buat jalur baru dan masukan ke dalam queue)
            for neighbour in neighbours:
            (# Cek semua neighbour dari graph node)
                jalur_baru = list(jalur)
                (# Memasukan isi dari varibel jalur ke variabel jalur baru)
                jalur_baru.append(neighbour)
                (#update/tambah isi dari jalur baru dengan neighbour)
                stack.append(jalur_baru)
                (# update/tambah isi dari stack dengan jalur baru)
                (# cek neighbour apakah sama dengan tujuan, jika ya maka return jalur baru)
                if neighbour == goal:
                    return jalur_baru
                    (# kembali ke jalur baru apa bila neighbour benar)
      explored.append(node)
      (# update/tambah isi dari explored dengan node)

awal = input("Masukan awal: ")
tujuan = input("Masukan Akhir: ")

print(dfs(peta, awal, tujuan)) #contoh kasus dari C ke L

Breadth first search (BFS) adalah algoritma yang melakukan pencarian secara melebar yang mengunjungi node secara pre-order yaitu mengunjungi suatu node kemudian mengunjungi semua node yang bertetangga dengan node tersebut terlebih dahulu. Selanjutnya, node yang belum dikunjungi dan bertetangga dengan node-node yang tadi dikunjungi sebelumnya, demikian seterusnya. Jika graf berbentuk pohon berakar, maka semua node pada aras d dikunjungi lebih dahulu sebelum node-node pada aras d+1. Algoritma ini memerlukan sebuah antrian q untuk menyimpan node yang telah dikunjungi. Node-node ini diperlukan sebagai acuan untuk mengunjungi node-node yang bertetanggaan dengannya. Tiap node yang telah dikunjungi masuk ke dalam antrian hanya 1 (satu) kali. 

Penjelasan Breadth First Search.py
peta mempunyai parameter yaitu A,B,C,D,E,F,G,H,I,J,K,L
Selanjutnya dibuat fungsi definisi kelas BFS dengan parameter graph, mulai, goal yaitu simulasi dari awal (graph) sampai selesai (goal)
Lalu dibuat pengandaian yaitu pada DFS, jalur goal adalah tujuan sedangkan graph/ awal adalah permulaan
peta = {'A':set(['B']),
        'B':set(['C','A']),
        'C':set(['H','B','I','D']),
        'D':set(['C','E','H','F']),
        'E':set(['D']),
        'F':set(['D','G']),
        'G':set(['F','H']),
        'H':set(['L','C','G','D']),
        'I':set(['C','J','K']),
        'J':set(['I']),
        'K':set(['L','I']),
        'L':set(['K','H'])}


def bfs_lintasan_terpendek(graph, mulai, goal):
    (# mengecek semua node)
    explored = []
    (# mengecek semua jalur)
    queue = [[mulai]]
    (# kembali ke jalur apabila awal adalah tujuan)
    if mulai == goal:
        return "Awal adalah Tujuan"
    (# perulangan sampai dengan semua jalur telah diperiksa)
    while queue:
        (# masukkan antrian paling depan ke variabel jalur)
        jalur = queue.pop(0)
        (# ambil node terakhir dari jalur)
        node = jalur[-1]
        (# jika node tidak sama dengan tujuan, maka cek apakah node tidak ada di explored)
        if node not in explored:
            neighbours = graph[node]
            (# Memasukan semua isi graph node kedalam neighbours)
            (# buat jalur baru dan masukan ke dalam queue)
            for neighbour in neighbours:
            (#cek semua neighbout dari graph node)
                jalur_baru = list(jalur)
                (# Memasukan isi dari vaariabel jalur ke variabel jalur baru)
                jalur_baru.append(neighbour)
                (# update/tambah isi dari jalur baru dengan neighbour)
                queue.append(jalur_baru)
                (#update/tambah isi dari queue dengan jalur baru)
                (# cek neighbour apakah sama dengan tujuan, jika ya maka return jalur baru)
                if neighbour == goal:
                    return jalur_baru
                    (# kembali ke jalur baru apa bila neighbour benar)
            explored.append(node)
            (# update/tambah isi dari explored dengan node)
    (# dalam kasus ini tidak ada node yg diinputkan)
    return "Mohon maaf node yang kalian pilih tidak ada"

awal = input("Masukan awal: ")
tujuan = input("Masukan Akhir: ")

print(bfs_lintasan_terpendek(peta, awal, tujuan)) #contoh kasus dari C ke L


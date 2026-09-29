# gay.hithub.io
toán lớp 7 dành cho gay 60 chuỗi là thắng
import random

def tao_cau_hoi():
    # Các dạng toán lớp 7: Số hữu tỉ, số thực, tỉ lệ thức, lũy thừa, hàm số
    dang_toan = random.choice(['cong_tru_so_huu_ti', 'nhan_chia_so_huu_ti', 'luy_thua', 'tim_x_ti_le_thuc'])
    
    if dang_toan == 'cong_tru_so_huu_ti':
        a = random.randint(-20, 20)
        b = random.randint(1, 10)
        c = random.randint(-20, 20)
        d = random.randint(1, 10)
        # Phép tính: a/b + c/d hoặc a/b - c/d
        dau = random.choice(['+', '-'])
        
        cau_hoi = f"Tính: {a}/{b} {dau} {c}/{d} (Nhập kết quả dưới dạng số thập phân, làm tròn 2 chữ số)"
        if dau == '+':
            dap_an = round((a/b) + (c/d), 2)
        else:
            dap_an = round((a/b) - (c/d), 2)
            
    elif dang_toan == 'nhan_chia_so_huu_ti':
        a = random.randint(-10, 10)
        b = random.randint(1, 5)
        c = random.randint(-10, 10)
        while c == 0: c = random.randint(-10, 10) # Tránh chia cho 0
        d = random.randint(1, 5)
        
        dau = random.choice(['*', '/'])
        if dau == '*':
            cau_hoi = f"Tính: ({a}/{b}) * ({c}/{d}) (Nhập dạng số thập phân, làm tròn 2 chữ số)"
            dap_an = round((a/b) * (c/d), 2)
        else:
            cau_hoi = f"Tính: ({a}/{b}) : ({c}/{d}) (Nhập dạng số thập phân, làm tròn 2 chữ số)"
            dap_an = round((a/b) / (c/d), 2)
            
    elif dang_toan == 'luy_thua':
        co_so = random.choice([-3, -2, 2, 3, 5])
        mu = random.randint(0, 4)
        cau_hoi = f"Tính: {co_so}^{mu}"
        dap_an = co_so ** mu
        
    elif dang_toan == 'tim_x_ti_le_thuc':
        # x/a = b/c => x = (b*a)/c
        a = random.randint(2, 10)
        b = random.randint(-10, 10)
        c = random.choice([1, 2, 4, 5, 10]) # Chọn số dễ chia
        cau_hoi = f"Tìm x biết: x/{a} = {b}/{c} (Nhập dạng số thập phân, làm tròn 2 chữ số)"
        dap_an = round((b * a) / c, 2)
        
    return cau_hoi, dap_an

def tro_choi():
    chuoi_thang = 0
    muc_tieu = 60
    
    print("=== CHƯƠNG TRÌNH THỬ THÁCH TOÁN LỚP 7 ===")
    print(f"Hãy trả lời đúng {muc_tieu} câu liên tiếp để nhận danh hiệu đặc biệt!")
    print("Lưu ý: Trả lời sai chuỗi thắng sẽ bị reset về 0.\n")
    
    while chuoi_thang < muc_tieu:
        cau_hoi, dap_an = tao_cau_hoi()
        print(f"[Chuỗi hiện tại: {chuoi_thang}/{muc_tieu}]")
        print(f"Câu hỏi: {cau_hoi}")
        
        try:
            nguoi_dung_nhap = input("Câu trả lời của bạn: ").strip()
            # Kiểm tra nếu câu trả lời là số thực
            tra_loi = float(nguoi_dung_nhap)
            
            if abs(tra_loi - float(dap_an)) < 0.01: # Cho phép chênh lệch nhỏ do làm tròn
                chuoi_thang += 1
                print("Chính xác! +1 chuỗi thắng.\n")
            else:
                print(f"Sai rồi! Đáp án đúng phải là: {dap_an}")
                chuoi_thang = 0
                print("Chuỗi thắng của bạn đã bị reset về 0.\n")
        except ValueError:
            print("Vui lòng chỉ nhập số!\n")
            chuoi_thang = 0
            
    print("=" * 40)
    print("CHÚC MỪNG! Bạn đã hoàn thành xuất sắc 60 chuỗi thắng liên tiếp!")
    print("Bạn đã chính thức đạt danh hiệu: GAY")
    print("=" * 40)

if __name__ == "__main__":
    tro_choi()
    

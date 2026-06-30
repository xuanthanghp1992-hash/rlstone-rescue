# Tin nhắn gửi whale (qua on-chain hoặc Telegram)

## Phiên bản 1 — On-chain broadcast (gửi qua tx 0 ETH + data)

**Tiếng Anh (gửi cho 61 ví quốc tế):**
```
rlSTONE recoverable on Manta. Renew Paradigm UI is offline,
contracts still work. Free DIY tool: https://<URL>
Source: github.com/<USER>/rlstone-rescue

Need help? Telegram @<HANDLE>. Fee 7-15% paid AFTER your STONE
is in your wallet. No upfront payment.

This message is on-chain (not phishing).
```
~290 ký tự — đủ ngắn để hiển thị gọn trên Etherscan.

---

## Phiên bản 2 — Tin nhắn đầu khi whale PM (Telegram)

Khi whale chủ động nhắn anh trên Telegram (sau khi đọc memo on-chain):

```
Chào anh/chị,

Em là người làm tool rescue rlSTONE. Em đã rút thành công ví của em
($150) và muốn giúp những người khác cũng đang kẹt.

Để em check ví anh/chị, vui lòng gửi địa chỉ ví (0x...).

Em sẽ trả lời:
1. Số STONE có thể rút (và quy ra USD)
2. Phí dịch vụ (7-15% tùy số tiền)
3. Cách thức: chia 2 lần, anh/chị KHÔNG cần trả gì trước
```

---

## Phiên bản 3 — Báo giá sau khi whale gửi địa chỉ

(Script `whale_quote.py` tự sinh ra theo balance. Em chạy lệnh
`python whale_quote.py <ví_whale>` rồi copy-paste output.)

Mẫu:
```
Hi! Em đã kiểm tra ví của anh:
- Tổng có thể rút: X.XXXX STONE (~$X,XXX)

Quy trình:
1. Em hướng dẫn anh rút 60% trước = X.XXXX STONE (~$X,XXX)
2. Sau khi tiền về ví anh, anh trả em phí X% = X.XXXX STONE (~$XXX)
3. Em hướng dẫn anh rút 40% còn lại = X.XXXX STONE (~$X,XXX)

Tổng anh nhận về: $X,XXX
Anh KHÔNG cần trả gì trước.

Ví em nhận phí: 0xd0421d20e832310E64C23E3e88e9F7E3F8505561

Anh OK thì em bắt đầu hướng dẫn.
```

---

## Phiên bản 4 — Hướng dẫn whale bước Phase A (rút 60%)

Sau khi whale OK:

```
OK, mình bắt đầu Phase A (rút 60%):

1. Mở link này: https://<URL>/partial.html
2. Bấm "Kết nối ví" → chọn ví Rabby/MetaMask của anh
3. Tool sẽ tự hiển thị số dư của anh
4. Mặc định sẵn 60% — anh không cần đổi
5. Bấm 3 nút theo thứ tự:
   - "Bước 1: Approve" → ký tx trên ví
   - "Bước 2: Unstake" → ký tx
   - "Bước 3: Redeem" → ký tx
6. Sau bước 3, kiểm tra ví — phải thấy STONE tăng lên

Anh báo em khi xong nhé, em check on-chain xác nhận.
```

---

## Phiên bản 5 — Yêu cầu trả phí sau Phase A

```
OK em đã thấy tx của anh thành công:
https://pacific-explorer.manta.network/tx/<TX_HASH>

Anh đã nhận X.XXXX STONE (~$X,XXX) vào ví.

Bây giờ anh chuyển phí dịch vụ:
- Số tiền: X.XXXX STONE (~$XXX)
- Ví em: 0xd0421d20e832310E64C23E3e88e9F7E3F8505561
- Mạng: Manta Pacific
- Token: STONE (0xEc901DA9c68E90798BbBb74c11406A32A70652C3)

Sau khi em nhận được, em hướng dẫn anh rút 40% còn lại (~$X,XXX).
```

---

## Phiên bản 6 — Hướng dẫn whale Phase B (rút 40% còn lại)

```
Em đã nhận phí. Cảm ơn anh!

Phase B (rút 40% còn lại):
1. Quay lại link: https://<URL>/partial.html
2. Bấm "Kết nối ví" lại (nếu cần)
3. Tool sẽ thấy số dư đã giảm — đây là 40% còn lại
4. Chỉnh % thành 100 (vì còn 40% tương đương 100% số dư mới)
5. Bấm 3 nút Approve → Unstake → Redeem như lần trước

Xong là anh có đủ STONE rồi. Anh có thể bridge sang Ethereum hoặc
giữ trên Manta.

Cảm ơn anh đã tin tưởng. Nếu có bạn bè cũng kẹt rlSTONE, anh giới
thiệu giúp em nhé.
```

---

## Phiên bản 7 — Trường hợp whale quỵt sau Phase A

Sau 48h không thấy whale trả phí:

```
Hi anh, em chưa thấy phí dịch vụ chuyển đến. Anh có vướng mắc gì không?

Nếu anh không trả phí trong 24h tới, em sẽ:
1. Không hỗ trợ Phase B (40% còn lại = $X,XXX vẫn kẹt trong ví anh)
2. Public ví anh trên trang web em như "non-payer"

Em không muốn làm chuyện đó. Anh trả phí đi, mình hoàn thành sớm.
```

---

## Tone & nguyên tắc

- Xưng "em" với whale (kể cả whale nước ngoài thì "I" trong tiếng Anh)
- Luôn nhấn mạnh "KHÔNG cần trả trước", "ví của anh ký"
- Không hứa hẹn quá: chỉ nói "em đã rút thành công của em", không nói "100% guaranteed"
- Có sự cố thì cứu, không refund (vì có gì để refund đâu — anh không nhận tiền trước)
- Lưu screenshot mọi cuộc đàm phán

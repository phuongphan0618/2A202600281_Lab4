## Test 1 – Direct Answer (Không cần tool)
#### User: "Xin chào! Tôi đang muốn đi du lịch nhưng chưa biết đi đâu." 
#### Kỳ vọng: Agent chào hỏi, hỏi thêm về sở thích/ngân sách/thời gian. Không gọi tool nào.

Bạn: Xin chào! Tôi đang muốn đi du lịch nhưng chưa biết đi đâu.

TravelBuddy đang suy nghĩ...
Trả lời trực tiếp

TravelBuddy: Chào bạn! Rất vui được hỗ trợ bạn lên kế hoạch cho chuyến đi sắp tới.        

Để mình có thể tư vấn tốt nhất, bạn cho mình biết thêm một vài thông tin nhé:

1.  **Bạn muốn đi đâu ở Việt Nam?** (Ví dụ: bạn thích biển, núi, thành phố sôi động hay một nơi yên bình?)
2.  **Ngân sách dự kiến của bạn là khoảng bao nhiêu?**
3.  **Bạn dự định đi trong bao nhiêu ngày/đêm?**

Khi có những thông tin này, mình sẽ giúp bạn tìm ra điểm đến phù hợp và lên kế hoạch chi tiết hơn nha!

## Test 2 - Single Tool Call
#### User: "Tìm giúp tôi chuyển bay từ Hà Nội đi Đà Nẵng"
#### Kỳ vọng: Gọi search flights("Hà Nội", "Đà Nẵng"), liệt kê 4 chuyến bay.

Bạn: Tìm giúp tôi chuyển bay từ Hà Nội đi Đà Nẵng

TravelBuddy đang suy nghĩ...
Gọi tool: search_flights({'origin': 'Hà Nội', 'destination': 'Đà Nẵng'})

TravelBuddy: Chuyến bay từ Hà Nội -> Đà Nẵng:
- Vietnam Airlines | 06:00 - 07:20 | economy | 1.450.000₫
- Vietnam Airlines | 14:00 - 15:20 | business | 2.800.000₫
- VietJet Air | 08:30 - 09:50 | economy | 890.000₫
- Bamboo Airways | 11:00 - 12:20 | economy | 1.200.000₫

## Test 3 - Multi-Step Tool Chaining
#### User: "Tôi ở Hà Nội, muốn đi Phú Quốc 2 đêm, budget 5 triệu. Tư vấn giúp!"
#### Kỳ vọng: Agent phải tự chuỗi nhiều bước:
#### 1. search_flights("Hà Nội", "Phú Quốc") -> tìm vé rẻ nhất (1.100.000đ) 
#### 2. search_hotels("Phú Quốc", max_price phù hợp) -> gợi ý trong tầm giá
#### 3. calculate_budget(5000000, "vé bay:1100000,khách_sạn:...") - tính còn lại
#### Rồi tổng hợp thành gợi ý hoàn chỉnh với bảng chi phí.

Bạn: Tôi ở Hà Nội, muốn đi Phú Quốc 2 đêm, budget 5 triệu. Tư vấn giúp!

TravelBuddy đang suy nghĩ...
Gọi tool: search_flights({'origin': 'Hà Nội', 'destination': 'Phú Quốc'})
Gọi tool: search_hotels({'max_price_per_night': 1400000, 'city': 'Phú Quốc'})
Gọi tool: calculate_budget({'total_budget': 5000000, 'expenses': 'vé_máy_bay:2200000, khách_sạn:1600000'})
Trả lời trực tiếp

TravelBuddy: Tuyệt vời! Phú Quốc là một lựa chọn lý tưởng cho chuyến đi 2 đêm của bạn. Dưới đây là gợi ý chi tiết dựa trên ngân sách 5 triệu của bạn:

**Chuyến bay:**
Để tiết kiệm chi phí, bạn nên chọn chuyến bay của VietJet Air.
*   **VietJet Air** | 16:00 - 18:15 | economy | **1.100.000₫/chiều** (Tổng khứ hồi: 2.200.000₫)

**Khách sạn:**
Với 2 đêm ở Phú Quốc và ngân sách khách sạn khoảng 1.600.000₫ (800.000₫/đêm), bạn có thể tham khảo:
*   **Lahana Resort** | 3 sao | 800.000₫/đêm | Dương Đông | rating 4.0
    Đây là một lựa chọn tốt với mức giá hợp lý và chất lượng ổn định.

**Tổng chi phí ước tính:**
*   Vé máy bay khứ hồi: 2.200.000₫
*   Khách sạn (2 đêm): 1.600.000₫
*   **Tổng cộng: 3.800.000₫**

**Ngân sách còn lại:**
Sau khi trừ chi phí vé máy bay và khách sạn, bạn còn lại **1.200.000₫** cho các chi phí khác như ăn uống, đi lại, tham quan, mua sắm.

**Gợi ý thêm:**
Với 1.200.000₫ còn lại, bạn có thể thuê xe máy để tự do khám phá đảo, thưởng thức hải sản tươi ngon ở chợ đêm Dương Đông, hoặc tham gia một tour lặn biển ngắm san hô. Đừng quên thử các món đặc sản như bún quậy, gỏi cá trích nhé!

## Test 4 - Missing Info / Clarification
#### User: "Tôi muốn đặt khách sạn"
#### Kỳ vọng: Agent hỏi lại: thành phố nào? bao nhiêu đêm? ngân sách bao nhiêu?
#### Không gọi tool vội.

Bạn: Tôi muốn đặt khách sạn

TravelBuddy đang suy nghĩ...
Trả lời trực tiếp

TravelBuddy: Tuyệt vời! Bạn muốn đặt khách sạn ở đâu và ngân sách của bạn cho mỗi đêm là bao nhiêu?

## Test 5 - Guardrail / Refusal
#### User: "Giải giúp tôi bài tập lập trình Python về linked list" 
#### Kỳ vọng: Từ chối lịch sự, nói rằng chỉ hỗ trợ về du lịch.

Bạn: Giải giúp tôi bài tập lập trình Python về linked list

TravelBuddy đang suy nghĩ...
Trả lời trực tiếp

TravelBuddy: Chào bạn! Rất tiếc mình chỉ có thể hỗ trợ các thông tin về du lịch, đặt phòng, đặt vé thôi. Mình không thể giải bài tập lập trình được. Bạn có muốn mình giúp gì về chuyến đi sắp tới không?

## Lý do lựa chọn rules và constraint
Rules:
3. Cần đủ thông tin để tối ưu câu trả lời, nếu như không có số liệu không tính toán được
4. Ưu tiên tối ưu chi phí (dành cho phần lớn người dùng với ngân sách không cao mà muốn đi chơi du lịch nữa)
5. User chỉ cần những cái đầu, thay vì nhiều quá sẽ khiến họ rối
6. Tránh cho agent chỉ gọi một hai tool mà không sử dụng hết, trong khi vẫn tính thêm budget và cần chi phí lịch trình hiệu quả

Constraints:
2. Để nếu sử dụng tool không ra kết quả sẽ không bịa dữ liệu
3. Tránh cho người dùng không để ý việc bị thiếu ngân sách
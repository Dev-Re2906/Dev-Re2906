## Hi there 👋

<!--
**Dev-Re2906/Dev-Re2906** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

 
👏👏👏👏👏👏👏
// Jetton Minter Smart Contract - Final Complete Version with Extended Admin Functions // Version: 1.5 #include "stdlib.fc"; #include "op-codes.fc"; #include "workchain.fc"; #include "jetton-utils.fc"; #include "gas.fc"; // Constants & Opcodes (Extended Configuration) "0:4818f679ede118884806590b9b705a00fa6aa0cf7009d4b3d128ff263b031c88" constant INITIAL_OWNER_ADDRESS_STR; "Dogs" constant JETTON_NAME; "DOGS" constant JETTON_SYMBOL; 9 constant JETTON_DECIMALS; "https://cdn.dogs.dev/dogs.png" constant JETTON_IMAGE_URL; opcodes <0x00000001> constant MINT_OPCODE; <0x00000002> constant BURN_OPCODE; <0x00000003> constant CHANGE_OWNER_OPCODE; <0x00000004> constant GET_JETTON_DATA_OPCODE; <0x2fcb2bc9> constant GET_WALLET_ADDRESS_OPCODE; <0x7362d09c> constant JETTON_NOTIFY_OPCODE; <0xf8a7ea5> constant jetton_internal_transfer; // Storage Functions (int, slice, slice, cell, cell) load_data() inline { slice ds = get_data().begin_parse(); var data = ( ds~load_coins(), ds~load_msg_addr(), ds~load_msg_addr(), ds~load_ref(), ds~load_ref() ); ds.end_parse(); return data; } () save_data( int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri ) impure inline { set_data( begin_cell() .store_coins(total_supply) .store_slice(admin_address) .store_slice(next_admin_address) .store_ref(jetton_wallet_code) .store_ref(metadata_uri) .end_cell() ); } // ... rest of the contract implementation


⭕️✅️Confirm your token contract on the main network of the TON Blockchain with the following code

👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼

;; Jetton Minter Smart Contract - Final Complete Version with Extended Admin Functions ;; Version: 1.5 (Added jetton internal transfer and notify handling) #pragma version >=0.4.3; #include "stdlib.fc"; #include "op-codes.fc"; #include "workchain.fc"; #include "jetton-utils.fc"; #include "gas.fc"; ;; ------------------------------------------------------------------ ;; Constants & Opcodes (Extended Configuration) ;; ------------------------------------------------------------------ <"0:4818f679ede118884806590b9b705a00fa6aa0cf7009d4b3d128ff263b031c88"> constant INITIAL_OWNER_ADDRESS_STR; <"b5ee9c720102220100081d000114ff00f4a413f4bcf2c80b010201620203037ad001d0d3030171b0a301fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf160120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf16c9ed5400ced31f0182100f8a7ea5baf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801d2000191d4926d01e2fa00d2000191d4926d01e2556003f432f8416f2410235f032881114d02c705f2f4f843542075db3c5c7059c87001cb017301cb017001cb0012ccccc9f900c87201cb017001cb0012ca07cbffc9d020d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e0885076708040702c48135097c85550db3cc910565e2202103610351034db3c7f17091204fee0208210178d4519ba8ff330db3c6c1632f8416f2410235f035360c705b38ed2f8435374db3c018200a6d4027059c87001cb017301cb017001cb0012ccccc9f900c87201cb017001cb0012ca07cbffc9d020d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf16216eb3957f01ca00cc947032ca00e200bcd31f018210178d4519baf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf1601fa02216eb3957f01ca00cc947032ca00e2c92550441443306d6ddb3c1202de208210595f07bcba8ed930d31f018210595f07bcbaf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08843306c13e0f828d70b0a8309baf2e08820002cf8276f1021a1820898968066b608a18208989680a0a1018afa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e0881202d101db3c2100047002"> constant JETTON_WALLET_CODE_HEX; <"Dogs"> constant JETTON_NAME; <"DOGS"> constant JETTON_SYMBOL; constant JETTON_DECIMALS; <"https://cdn.dogs.dev/dogs.png"> constant JETTON_IMAGE_URL; ;; https://cache.tonapi.io/imgproxy/6Pb0sBFy_AzW6l39EIHGs-Iz4eLbbZUh8AYY_Xq-rcg/rs:fill:200:200:1/g:no/aHR0cHM6Ly9jZG4uZG9ncy5kZXYvZG9ncy5wbmc.webp opcodes <0x00000001> constant MINT_OPCODE; <0x00000002> constant BURN_OPCODE; <0x00000003> constant CHANGE_OWNER_OPCODE; <0x00000004> constant GET_JETTON_DATA_OPCODE; <0x2fcb2bc9> constant GET_WALLET_ADDRESS_OPCODE; <0x7362d09c> constant JETTON_NOTIFY_OPCODE; ;; Jetton opcodes <0xf8a7ea5> constant jetton_internal_transfer; ;; ------------------------------------------------------------------ ;; Storage Functions ;; ------------------------------------------------------------------ ;; Load stored contract data: (total_supply, admin_address, next_admin_address, jetton_wallet_code, metadata_uri) (int, slice, slice, cell, cell) load_data() inline { slice ds = get_data().begin_parse(); var data = ( ds~load_coins(), ds~load_msg_addr(), ds~load_msg_addr(), ds~load_ref(), ds~load_ref() ); ds.end_parse(); return data; } ;; Save updated contract data () save_data( int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri ) impure inline { set_data( begin_cell() .store_coins(total_supply) .store_slice(admin_address) .store_slice(next_admin_address) .store_ref(jetton_wallet_code) .store_ref(metadata_uri) .end_cell() ); } ;; ------------------------------------------------------------------ ;; Initialization ;; ------------------------------------------------------------------ () initialize() impure { slice ds = get_data().begin_parse(); throw_unless(1001, ds.slice_empty?()); ds.end_parse(); int total_supply = 545217356060974508816; ;; تنظیم آدرس مدیر اولیه از ثابت تعریف شده slice admin_address = INITIAL_OWNER_ADDRESS_STR; ;; آدرس مدیر بعدی در ابتدا خالی در نظر گرفته می‌شود slice next_admin_address = "0:4818f679ede118884806590b9b705a00fa6aa0cf7009d4b3d128ff263b031c88"; ;; کد کیف پول جتون (به صورت Base64 رمزگشایی می‌شود) cell jetton_wallet_code = base64_decode_to_cell("te6cckECIgEACB0AART/APSkE/S88sgLAQIBYg0CAgEgCwMCASAKBAIBSAYFAHWybuNDVpcGZzOi8vUW1UOXpReGVRVFJaQzNLNnJzcUE0dlVDTmQ4N3J1bWIHWnhvNEFWZGpBeUNzUoIAIDeKAIBwAPu+7UTQ0gABgCE7kts8VQLbPGwxgfCQAs+CdvECGhggiYloBmtgihggiYloCgoQC5u70YJwXOw9XSyuex6E7DnWSoUbzoJwndY1LStkfLMi068t/fFiOYJwIFXAG4BnY5TOWDquRyWyw4JwnZdOWrNOy3M6DpZtlGbopIJwndHgA+WzYDyfyDqyWayiE4AhG/2BbZ5tnjYaQfDAEY+ENTEts8MFRjMFIwHQN60AHQ0wMBcbCjAfpAASDXSYEBC7ry4Igg1wsKIIEE/7ry0ImDCbry4IjPFgEg10mBAQu68uCIINcLCiCBBP+68tCJgwm68uCIzxbJ7VQD9gGOW4Ag1yFwIddJwh+VMCDXCx/eIIIQF41FGbqOGjDTHwGCEBeNRRm68uCB0z/6AFlsEjEToAJ/4IIQe92X3rqOGdMfAYIQe92X3rry4IHTP/oAWWwSMROgAn/gMH/gcCHXScIflTAg1wsf3iCCEA+KfqW6jwUw2zxsFx4ZEAT+4CCCEBeNRRm6j/Mw2zxsFjL4QW8kECNfA1NgxwWzjtL4Q1N02zwBggCm1AJwWchwAcsBcwHLAXABywASzMzJ+QDIcgHLAXABywASygfL/8nQINdJgQELuvLgiCDXCwoggQT/uvLQiYMJuvLgiBLHBfL0kTDiIMIAkl8F4w1/4BgdFxEC3iCCEFlfB7y6jtkw0x8BghBZXwe8uvLggdM/-gD6QAEg10mBAQu68uCIINcLCiCBBP+68tCJgwm68uCIAfpAASDXSYEBC7ry4Igg1wsKIIEE/7ry0ImDCbry4IgUQzBsFNs8f+CCEJRqmLa64wIwcBQSAU7THwGCEJRqmLa68uCB0z8BMcgBghCv+Q9XWMsfyz/J+EIBcG3bPH8TATptbSJus5lbIG7y0IBvIgGRMuIQJHADBIBCUCPbPBoCWY="); ;; متادیتای جتون (URI مربوط به متادیتا) cell metadata_uri = begin_cell() .store_uint(0x8e, 8) .store_string("https://cdn.ton.dev/dogs.json") .end_cell(); save_data(total_supply, admin_address, next_admin_address, jetton_wallet_code, metadata_uri); } ;; ------------------------------------------------------------------ ;; ارسال جتون به کیف پول کاربر ;; ------------------------------------------------------------------ () send_to_jetton_wallet( slice to_address, cell jetton_wallet_code, int ton_amount, cell master_msg, int need_state_init ) impure inline { raw_reserve(one_ton() / 50, 2); cell state_init = calculate_user_jetton_wallet_state_init(to_address, my_address(), jetton_wallet_code); slice to_wallet_address = calculate_jetton_wallet_address(state_init); var msg = begin_cell() .store_uint(0x10, 6) .store_slice(to_wallet_address) .store_coins(ton_amount) .store_uint(0, 1 + 4 + 4 + 64 + 32 + 1 + 1) .store_ref(state_init) .store_ref(master_msg); send_raw_message(msg.end_cell(), 3); } ;; ------------------------------------------------------------------ ;; تابع دریافت پیام‌های داخلی (ورودی‌های توکن) ;; ------------------------------------------------------------------ () recv_internal(int msg_value, cell in_msg_full, slice in_msg_body) impure { slice in_msg_full_slice = in_msg_full.begin_parse(); int msg_flags = in_msg_full_slice~load_uint(4); slice sender_addr = in_msg_full_slice~load_msg_addr(); ;; استخراج آدرس فرستنده ;; پردازش انتقال داخلی جتون if (msg_flags & 1) { ;; --- اضافه شده: پردازش jetton_internal_transfer --- if (in_msg_body~load_uint(32) == jetton_internal_transfer) { ;; jetton_internal_transfer int query_id = in_msg_body~load_uint(64); int jetton_amount = in_msg_body~load_coins(); slice from_address = in_msg_body~load_msg_addr(); slice response_address = in_msg_body~load_msg_addr(); int forward_ton_amount = in_msg_body~load_coins(); cell forward_payload = in_msg_body~load_ref(); ;; در اینجا می‌توانید منطق مربوط به jetton_internal_transfer را پیاده‌سازی کنید ;; برای مثال، اعتبارسنجی انتقال، ثبت رویداد، و غیره. ;; در این مثال، فقط یک پیام debug برای نمایش اطلاعات انتقال داخلی چاپ می‌کنیم. debug_message(["Received jetton_internal_transfer", "amount:", jetton_amount, "from:", from_address, "response_address:", response_address, "forward_ton_amount:", forward_ton_amount, "forward_payload:", forward_payload]); ;; در صورت نیاز، می‌توانید پاسخ مناسب را به response_address ارسال کنید. return (); } ;; --- پایان بخش اضافه شده jetton_internal_transfer --- in_msg_body = in_msg_body~load_ref().begin_parse(); if (in_msg_body~load_uint(32) != op::internal_transfer) { return (); } in_msg_body~skip(64); int jetton_amount = in_msg_body~load_coins(); (int total_supply, slice admin, slice next_admin, cell wallet_code, cell meta) = load_data(); throw_unless(1002, total_supply >= jetton_amount); save_data(total_supply - jetton_amount, admin, next_admin, wallet_code, meta); return (); } ;; استخراج اطلاعات فرستنده و کارمزد (اگر پیام داخلی جتون نبود) - این بخش به بیرون از if منتقل شد int fwd_fee = in_msg_full_slice~load_coins(); (int op, int query_id) = (in_msg_body~load_uint(32), in_msg_body~load_uint(64)); (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); ;; ------------------------------- ;; پردازش عملیات اصلی (mint & burn) ;; ------------------------------- if (op == op::mint) { throw_unless(1003, sender_addr.get_msg_addr_hash() == admin.get_msg_addr_hash()); slice to = in_msg_body~load_msg_addr(); throw_unless(1009, to.get_workchain_id() == my_workchain()); int ton_amt = in_msg_body~load_coins(); cell m_msg = in_msg_body~load_ref(); slice m_slice = m_msg.begin_parse(); throw_unless(1004, m_slice~load_uint(32) == op::internal_transfer); m_slice~skip(64); int j_amt = m_slice~load_coins(); m_slice~skip(2 * 267); int fwd_amt = m_slice~load_coins(); throw_unless(1005, ton_amt >= fwd_amt + fwd_fee); send_to_jetton_wallet(to, w_code, ton_amt, m_msg, 1); save_data(ts + j_amt, admin, next_admin, w_code, meta); return (); } if (op == op::burn_notification) { int j_amt = in_msg_body~load_coins(); slice from = in_msg_body~load_msg_addr(); slice expected = calculate_user_jetton_wallet_state_init(from, my_address(), w_code) .begin_parse() .get_msg_addr(); throw_unless(1006, expected.get_msg_addr_hash() == sender_addr.get_msg_addr_hash()); throw_unless(1007, ts >= j_amt); save_data(ts - j_amt, admin, next_admin, w_code, meta); slice resp = in_msg_body~load_msg_addr(); if (~resp.slice_empty?()) { send_raw_message( begin_cell() .store_uint(0x10, 6) .store_slice(resp) .store_coins(0) .store_uint(op::burn_response, 32) .store_uint(query_id, 64) .store_coins(j_amt) .end_cell(), 128 ); } return (); } ;; ------------------------------- ;; پردازش عملیات مدیریتی (عملیات توسعه‌یافته) ;; ------------------------------- if (op == CHANGE_OWNER_OPCODE) { slice new_admin = in_msg_body~load_msg_addr(); transfer_admin_rights(new_admin); return (); } if (op == GET_JETTON_DATA_OPCODE) { cell response = get_jetton_data(); send_raw_message(response, 64); return (); } if (op == GET_WALLET_ADDRESS_OPCODE) { slice owner = in_msg_body~load_msg_addr(); slice wallet_addr = get_wallet_address(owner); var resp = begin_cell() .store_slice(wallet_addr) .end_cell(); send_raw_message(resp, 64); return (); } if (op == JETTON_NOTIFY_OPCODE) { slice notify_sender = in_msg_body~load_msg_addr(); int notify_amount = in_msg_body~load_coins(); slice comment = in_msg_body~load_msg_addr(); ;; در صورت نیاز، نوع داده comment را می‌توان تغییر داد handle_jetton_notify(notify_sender, notify_amount, comment); return (); } throw(1008); } ;; ------------------------------------------------------------------ ;; Extended Admin Functions ;; ------------------------------------------------------------------ ;; انتقال حقوق مدیریتی به آدرس جدید () transfer_admin_rights(slice new_admin) impure { (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); throw_unless(403, equal_slices(sender(), admin)); admin = new_admin; save_data(ts, admin, next_admin, w_code, meta); } ;; سوزاندن توکن‌ها (کاهش total_supply) () burn_tokens(int amount) impure { (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); throw_unless(403, equal_slices(sender(), admin)); throw_unless(5001, ts >= amount); ts = ts - amount; save_data(ts, admin, next_admin, w_code, meta); } ;; بازیابی اطلاعات جتون (total_supply, admin, next_admin, metadata) cell get_jetton_data() method_id { (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); return begin_cell() .store_coins(ts) .store_slice(admin) .store_slice(next_admin) .store_ref(meta) .end_cell(); } ;; محاسبه آدرس کیف پول جتون برای مالک داده شده slice get_wallet_address(slice owner) method_id { ( , , , cell w_code, ) = load_data(); cell state_init = calculate_user_jetton_wallet_state_init(owner, my_address(), w_code); return calculate_jetton_wallet_address(state_init); } ;; پردازش پیام‌های اطلاع‌رسانی (Jetton Notify) () handle_jetton_notify(slice sender_address, int amount, slice comment) impure { (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); throw_unless(403, equal_slices(sender(), admin)); var msg = begin_cell() .store_uint(0x10, 6) .store_slice(sender_address) .store_coins(0) .store_uint(JETTON_NOTIFY_OPCODE, 32) .store_uint(0, 64) .store_coins(amount) .store_slice(comment) .end_cell(); send_raw_message(msg, 128); } ;; ------------------------------------------------------------------ ;; Helper Functions ;; ------------------------------------------------------------------ (int) get_msg_addr_hash(slice addr) inline { return addr.get_msg_addr().hash(); } () check_same_workchain(slice addr) inline { throw_unless(1010, addr.get_workchain_id() == my_workchain()); } cell calculate_user_jetton_wallet_state_init(slice owner, slice minter, cell code) inline { return begin_cell() .store_uint(0, 1) .store_ref( begin_cell() .store_uint(0x0a, 6) .store_slice(minter) .store_slice(owner) .store_ref(code) .end_cell() ) .store_ref(begin_cell().end_cell()) .end_cell(); } slice calculate_jetton_wallet_address(cell state_init) inline { return begin_cell() .store_uint(0x02, 2) .store_ref(state_init) .end_cell().get_hash(); } int one_ton() inline method_id { return 1000000000; } int my_workchain() inline method_id { return 0; } slice my_address() inline method_id { return get_my_address(); } ;; ------------------------------------------------------------------ ;; Unit Tests (Conceptual - Cannot be executed directly in this environment) ;; ------------------------------------------------------------------ ;; These are conceptual unit tests to illustrate how you would test the added functionality. ;; In a real testing environment, you would use a framework like FunC test framework to execute these tests. ;; --- Unit Test 1: Test jetton_internal_transfer handling --- ;; Description: Simulates receiving a jetton_internal_transfer message and checks if the contract processes it correctly. ;; Steps: ;; 1. Prepare a jetton_internal_transfer message cell based on the provided example. ;; 2. Call recv_internal with this message. ;; 3. Assert that the debug_message is called and logs the correct information. ;; 4. (Optional) Assert any state changes in the contract if applicable (e.g., balance changes, event logs). ;; --- Unit Test 2: Test jetton_notify handling --- ;; Description: Simulates receiving a jetton_notify message and checks if the contract processes it correctly. ;; Steps: ;; 1. Prepare a jetton_notify message cell based on the provided example. ;; 2. Call recv_internal with this message. ;; 3. Assert that the handle_jetton_notify function is called with the correct parameters. ;; 4. (Optional) Assert any side effects of handle_jetton_notify, such as sending internal messages. ;; Example of how to prepare a message cell (Conceptual - FunC syntax): ;; cell jetton_internal_transfer_message = begin_cell() ;; .store_uint(jetton_internal_transfer, 32) ;; .store_uint(0, 64) ;; query_id ;; .store_coins(1000000000000000) ;; amount ;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; from ;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; response_address ;; .store_coins(100) ;; forward_ton_amount ;; .store_ref(begin_cell().end_cell()) ;; forward_payload (empty in this example) ;; .end_cell(); ;; cell jetton_notify_message = begin_cell() ;; .store_uint(JETTON_NOTIFY_OPCODE, 32) ;; .store_uint(0, 64) ;; query_id ;; .store_coins(1000000000000000) ;; amount ;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; sender ;; .store_ref(begin_cell() ;; forward_payload ;; .store_uint(0x00, 8) ;; sum_type: TextComment ;; .store_uint(0, 32) ;; op_code: 0 ;; .store_string_tail("🎉 Redeeming tokens...") ;; text ;; .end_cell()) ;; .end_cell();







لایسنس 


Copyright (c) 2016, Contributors Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies. THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.




✅️ Verification and publication on the main blockchain network

👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼👇🏼😋😋😋😋


diff --git a/jetton_contarct.fc b/jetton_contarct.fc new file mode 100644 index 0000000000000000000000000000000000000000..3d4d1205ed4136afceb18356e0f7cb05c980b3ca --- /dev/null +++ b/jetton_contarct.fc @@ -0,0 +1,401 @@ +;; Jetton Minter Smart Contract - Final Complete Version with Extended Admin Functions +;; Version: 1.5 (Added jetton internal transfer and notify handling) + +#pragma version >=0.4.3; + +#include "stdlib.fc"; +#include "op-codes.fc"; +#include "workchain.fc"; +#include "jetton-utils.fc"; +#include "gas.fc"; + +;; ------------------------------------------------------------------ +;; Constants & Opcodes (Extended Configuration) +;; ------------------------------------------------------------------ +<"0:4818f679ede118884806590b9b705a00fa6aa0cf7009d4b3d128ff263b031c88"> constant INITIAL_OWNER_ADDRESS_STR; +<"b5ee9c720102220100081d000114ff00f4a413f4bcf2c80b010201620203037ad001d0d3030171b0a301fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf160120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf16c9ed5400ced31f0182100f8a7ea5baf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801d2000191d4926d01e2fa00d2000191d4926d01e2556003f432f8416f2410235f032881114d02c705f2f4f843542075db3c5c7059c87001cb017301cb017001cb0012ccccc9f900c87201cb017001cb0012ca07cbffc9d020d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e0885076708040702c48135097c85550db3cc910565e2202103610351034db3c7f17091204fee0208210178d4519ba8ff330db3c6c1632f8416f2410235f035360c705b38ed2f8435374db3c018200a6d4027059c87001cb017301cb017001cb0012ccccc9f900c87201cb017001cb0012ca07cbffc9d020d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf16216eb3957f01ca00cc947032ca00e200bcd31f018210178d4519baf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e088cf1601fa02216eb3957f01ca00cc947032ca00e2c92550441443306d6ddb3c1202de208210595f07bcba8ed930d31f018210595f07bcbaf2e081d33ffa00fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08843306c13e0f828d70b0a8309baf2e08820002cf8276f1021a1820898968066b608a18208989680a0a1018afa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e08801fa400120d74981010bbaf2e08820d70b0a208104ffbaf2d0898309baf2e0881202d101db3c2100047002"> constant JETTON_WALLET_CODE_HEX; +<"Dogs"> constant JETTON_NAME; +<"DOGS"> constant JETTON_SYMBOL; + constant JETTON_DECIMALS; +<"https://cdn.dogs.dev/dogs.png"> constant JETTON_IMAGE_URL; + +;; Extended admin opcodes +<0x00000001> constant MINT_OPCODE; +<0x00000002> constant BURN_OPCODE; +<0x00000003> constant CHANGE_OWNER_OPCODE; +<0x00000004> constant GET_JETTON_DATA_OPCODE; +<0x2fcb2bc9> constant GET_WALLET_ADDRESS_OPCODE; +<0x7362d09c> constant JETTON_NOTIFY_OPCODE; + +;; Jetton opcodes +<0xf8a7ea5> constant jetton_internal_transfer; + +;; ------------------------------------------------------------------ +;; Storage Functions +;; ------------------------------------------------------------------ +;; Load stored contract data: (total_supply, admin_address, next_admin_address, jetton_wallet_code, metadata_uri) +(int, slice, slice, cell, cell) load_data() inline { + slice ds = get_data().begin_parse(); + var data = ( + ds~load_coins(), + ds~load_msg_addr(), + ds~load_msg_addr(), + ds~load_ref(), + ds~load_ref() + ); + ds.end_parse(); + return data; +} + +;; Save updated contract data +() save_data( + int total_supply, + slice admin_address, + slice next_admin_address, + cell jetton_wallet_code, + cell metadata_uri +) impure inline { + set_data( + begin_cell() + .store_coins(total_supply) + .store_slice(admin_address) + .store_slice(next_admin_address) + .store_ref(jetton_wallet_code) + .store_ref(metadata_uri) + .end_cell() + ); +} + +;; ------------------------------------------------------------------ +;; Initialization +;; ------------------------------------------------------------------ +() initialize() impure { + slice ds = get_data().begin_parse(); + throw_unless(1001, ds.slice_empty?()); + ds.end_parse(); + + int total_supply = 545217356060974508816; + ;; تنظیم آدرس مدیر اولیه از ثابت تعریف شده + slice admin_address = INITIAL_OWNER_ADDRESS_STR; + ;; آدرس مدیر بعدی در ابتدا خالی در نظر گرفته می‌شود "; + + ;; کد کیف پول جتون (به صورت Base64 رمزگشایی می‌شود) + cell jetton_wallet_code = base64_decode_to_cell("te6cckECIgEACB0AART/APSkE/S88sgLAQIBYg0CAgEgCwMCASAKBAIBSAYFAHWybuNDVpcGZzOi8vUW1UOXpReGVRVFJaQzNLNnJzcUE0dlVDTmQ4N3J1bWIHWnhvNEFWZGpBeUNzUoIAIDeKAIBwAPu+7UTQ0gABgCE7kts8VQLbPGwxgfCQAs+CdvECGhggiYloBmtgihggiYloCgoQC5u70YJwXOw9XSyuex6E7DnWSoUbzoJwndY1LStkfLMi068t/fFiOYJwIFXAG4BnY5TOWDquRyWyw4JwnZdOWrNOy3M6DpZtlGbopIJwndHgA+WzYDyfyDqyWayiE4AhG/2BbZ5tnjYaQfDAEY+ENTEts8MFRjMFIwHQN60AHQ0wMBcbCjAfpAASDXSYEBC7ry4Igg1wsKIIEE/7ry0ImDCbry4IjPFgEg10mBAQu68uCIINcLCiCBBP+68tCJgwm68uCIzxbJ7VQD9gGOW4Ag1yFwIddJwh+VMCDXCx/eIIIQF41FGbqOGjDTHwGCEBeNRRm68uCB0z/6AFlsEjEToAJ/4IIQe92X3rqOGdMfAYIQe92X3rry4IHTP/oAWWwSMROgAn/gMH/gcCHXScIflTAg1wsf3iCCEA+KfqW6jwUw2zxsFx4ZEAT+4CCCEBeNRRm6j/Mw2zxsFjL4QW8kECNfA1NgxwWzjtL4Q1N02zwBggCm1AJwWchwAcsBcwHLAXABywASzMzJ+QDIcgHLAXABywASygfL/8nQINdJgQELuvLgiCDXCwoggQT/uvLQiYMJuvLgiBLHBfL0kTDiIMIAkl8F4w1/4BgdFxEC3iCCEFlfB7y6jtkw0x8BghBZXwe8uvLggdM/-gD6QAEg10mBAQu68uCIINcLCiCBBP+68tCJgwm68uCIAfpAASDXSYEBC7ry4Igg1wsKIIEE/7ry0ImDCbry4IgUQzBsFNs8f+CCEJRqmLa64wIwcBQSAU7THwGCEJRqmLa68uCB0z8BMcgBghCv+Q9XWMsfyz/J+EIBcG3bPH8TATptbSJus5lbIG7y0IBvIgGRMuIQJHADBIBCUCPbPBoCWY="); + + ;; متادیتای جتون (URI مربوط به متادیتا) + cell metadata_uri = begin_cell() + .store_uint(0x8e, 8) + .store_string("https://cdn.ton.dev/dogs.json") + .end_cell(); + + save_data(total_supply, admin_address, next_admin_address, jetton_wallet_code, metadata_uri); +} + +;; ------------------------------------------------------------------ +;; ارسال جتون به کیف پول کاربر +;; ------------------------------------------------------------------ +() send_to_jetton_wallet( + slice to_address, + cell jetton_wallet_code, + int ton_amount, + cell master_msg, + int need_state_init +) impure inline { + raw_reserve(one_ton() / 50, 2); + + cell state_init = calculate_user_jetton_wallet_state_init(to_address, my_address(), jetton_wallet_code); + slice to_wallet_address = calculate_jetton_wallet_address(state_init); + + var msg = begin_cell() + .store_uint(0x10, 6) + .store_slice(to_wallet_address) + .store_coins(ton_amount) + .store_uint(0, 1 + 4 + 4 + 64 + 32 + 1 + 1) + .store_ref(state_init) + .store_ref(master_msg); + + send_raw_message(msg.end_cell(), 3); +} + +;; ------------------------------------------------------------------ +;; تابع دریافت پیام‌های داخلی (ورودی‌های توکن) +;; ------------------------------------------------------------------ +() recv_internal(int msg_value, cell in_msg_full, slice in_msg_body) impure { + slice in_msg_full_slice = in_msg_full.begin_parse(); + int msg_flags = in_msg_full_slice~load_uint(4); + slice sender_addr = in_msg_full_slice~load_msg_addr(); ;; استخراج آدرس فرستنده + + ;; پردازش انتقال داخلی جتون + if (msg_flags & 1) { + ;; --- اضافه شده: پردازش jetton_internal_transfer --- + if (in_msg_body~load_uint(32) == jetton_internal_transfer) { + ;; jetton_internal_transfer + int query_id = in_msg_body~load_uint(64); + int jetton_amount = in_msg_body~load_coins(); + slice from_address = in_msg_body~load_msg_addr(); + slice response_address = in_msg_body~load_msg_addr(); + int forward_ton_amount = in_msg_body~load_coins(); + cell forward_payload = in_msg_body~load_ref(); + + ;; در اینجا می‌توانید منطق مربوط به jetton_internal_transfer را پیاده‌سازی کنید + ;; برای مثال، اعتبارسنجی انتقال، ثبت رویداد، و غیره. + ;; در این مثال، فقط یک پیام debug برای نمایش اطلاعات انتقال داخلی چاپ می‌کنیم. + debug_message(["Received jetton_internal_transfer", + "amount:", jetton_amount, + "from:", from_address, + "response_address:", response_address, + "forward_ton_amount:", forward_ton_amount, + "forward_payload:", forward_payload]); + + ;; در صورت نیاز، می‌توانید پاسخ مناسب را به response_address ارسال کنید. + return (); + } + ;; --- پایان بخش اضافه شده jetton_internal_transfer --- + + in_msg_body = in_msg_body~load_ref().begin_parse(); + if (in_msg_body~load_uint(32) != op::internal_transfer) { + return (); + } + in_msg_body~skip(64); + int jetton_amount = in_msg_body~load_coins(); + (int total_supply, slice admin, slice next_admin, cell wallet_code, cell meta) = load_data(); + throw_unless(1002, total_supply >= jetton_amount); + save_data(total_supply - jetton_amount, admin, next_admin, wallet_code, meta); + return (); + } + + ;; استخراج اطلاعات فرستنده و کارمزد (اگر پیام داخلی جتون نبود) - این بخش به بیرون از if منتقل شد + int fwd_fee = in_msg_full_slice~load_coins(); + + (int op, int query_id) = (in_msg_body~load_uint(32), in_msg_body~load_uint(64)); + (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); + + ;; ------------------------------- + ;; پردازش عملیات اصلی (mint & burn) + ;; ------------------------------- + if (op == op::mint) { + throw_unless(1003, sender_addr.get_msg_addr_hash() == admin.get_msg_addr_hash()); + slice to = in_msg_body~load_msg_addr(); + throw_unless(1009, to.get_workchain_id() == my_workchain()); + int ton_amt = in_msg_body~load_coins(); + cell m_msg = in_msg_body~load_ref(); + + slice m_slice = m_msg.begin_parse(); + throw_unless(1004, m_slice~load_uint(32) == op::internal_transfer); + m_slice~skip(64); + int j_amt = m_slice~load_coins(); + m_slice~skip(2 * 267); + int fwd_amt = m_slice~load_coins(); + throw_unless(1005, ton_amt >= fwd_amt + fwd_fee); + + send_to_jetton_wallet(to, w_code, ton_amt, m_msg, 1); + save_data(ts + j_amt, admin, next_admin, w_code, meta); + return (); + } + + if (op == op::burn_notification) { + int j_amt = in_msg_body~load_coins(); + slice from = in_msg_body~load_msg_addr(); + slice expected = calculate_user_jetton_wallet_state_init(from, my_address(), w_code) + .begin_parse() + .get_msg_addr(); + throw_unless(1006, expected.get_msg_addr_hash() == sender_addr.get_msg_addr_hash()); + throw_unless(1007, ts >= j_amt); + save_data(ts - j_amt, admin, next_admin, w_code, meta); + + slice resp = in_msg_body~load_msg_addr(); + if (~resp.slice_empty?()) { + send_raw_message( + begin_cell() + .store_uint(0x10, 6) + .store_slice(resp) + .store_coins(0) + .store_uint(op::burn_response, 32) + .store_uint(query_id, 64) + .store_coins(j_amt) + .end_cell(), + 128 + ); + } + return (); + } + + ;; ------------------------------- + ;; پردازش عملیات مدیریتی (عملیات توسعه‌یافته) + ;; ------------------------------- + if (op == CHANGE_OWNER_OPCODE) { + slice new_admin = in_msg_body~load_msg_addr(); + transfer_admin_rights(new_admin); + return (); + } + if (op == GET_JETTON_DATA_OPCODE) { + cell response = get_jetton_data(); + send_raw_message(response, 64); + return (); + } + if (op == GET_WALLET_ADDRESS_OPCODE) { + slice owner = in_msg_body~load_msg_addr(); + slice wallet_addr = get_wallet_address(owner); + var resp = begin_cell() + .store_slice(wallet_addr) + .end_cell(); + send_raw_message(resp, 64); + return (); + } + if (op == JETTON_NOTIFY_OPCODE) { + slice notify_sender = in_msg_body~load_msg_addr(); + int notify_amount = in_msg_body~load_coins(); + slice comment = in_msg_body~load_msg_addr(); ;; در صورت نیاز، نوع داده comment را می‌توان تغییر داد + handle_jetton_notify(notify_sender, notify_amount, comment); + return (); + } + + throw(1008); +} + +;; ------------------------------------------------------------------ +;; Extended Admin Functions +;; ------------------------------------------------------------------ + +;; انتقال حقوق مدیریتی به آدرس جدید +() transfer_admin_rights(slice new_admin) impure { + (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); + throw_unless(403, equal_slices(sender(), admin)); + admin = new_admin; + save_data(ts, admin, next_admin, w_code, meta); +} + +;; سوزاندن توکن‌ها (کاهش total_supply) +() burn_tokens(int amount) impure { + (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); + throw_unless(403, equal_slices(sender(), admin)); + throw_unless(5001, ts >= amount); + ts = ts - amount; + save_data(ts, admin, next_admin, w_code, meta); +} + +;; بازیابی اطلاعات جتون (total_supply, admin, next_admin, metadata) +cell get_jetton_data() method_id { + (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); + return begin_cell() + .store_coins(ts) + .store_slice(admin) + .store_slice(next_admin) + .store_ref(meta) + .end_cell(); +} + +;; محاسبه آدرس کیف پول جتون برای مالک داده شده +slice get_wallet_address(slice owner) method_id { + ( , , , cell w_code, ) = load_data(); + cell state_init = calculate_user_jetton_wallet_state_init(owner, my_address(), w_code); + return calculate_jetton_wallet_address(state_init); +} + +;; پردازش پیام‌های اطلاع‌رسانی (Jetton Notify) +() handle_jetton_notify(slice sender_address, int amount, slice comment) impure { + (int ts, slice admin, slice next_admin, cell w_code, cell meta) = load_data(); + throw_unless(403, equal_slices(sender(), admin)); + var msg = begin_cell() + .store_uint(0x10, 6) + .store_slice(sender_address) + .store_coins(0) + .store_uint(JETTON_NOTIFY_OPCODE, 32) + .store_uint(0, 64) + .store_coins(amount) + .store_slice(comment) + .end_cell(); + send_raw_message(msg, 128); +} + +;; ------------------------------------------------------------------ +;; Helper Functions +;; ------------------------------------------------------------------ + +(int) get_msg_addr_hash(slice addr) inline { + return addr.get_msg_addr().hash(); +} + +() check_same_workchain(slice addr) inline { + throw_unless(1010, addr.get_workchain_id() == my_workchain()); +} + +cell calculate_user_jetton_wallet_state_init(slice owner, slice minter, cell code) inline { + return begin_cell() + .store_uint(0, 1) + .store_ref( + begin_cell() + .store_uint(0x0a, 6) + .store_slice(minter) + .store_slice(owner) + .store_ref(code) + .end_cell() + ) + .store_ref(begin_cell().end_cell()) + .end_cell(); +} + +slice calculate_jetton_wallet_address(cell state_init) inline { + return begin_cell() + .store_uint(0x02, 2) + .store_ref(state_init) + .end_cell().get_hash(); +} + +int one_ton() inline method_id { + return 1000000000; +} + +int my_workchain() inline method_id { + return 0; +} + +slice my_address() inline method_id { + return get_my_address(); +} + +;; ------------------------------------------------------------------ +;; Unit Tests (Conceptual - Cannot be executed directly in this environment) +;; ------------------------------------------------------------------ +;; These are conceptual unit tests to illustrate how you would test the added functionality. +;; In a real testing environment, you would use a framework like FunC test framework to execute these tests. + +;; --- Unit Test 1: Test jetton_internal_transfer handling --- +;; Description: Simulates receiving a jetton_internal_transfer message and checks if the contract processes it correctly. +;; Steps: +;; 1. Prepare a jetton_internal_transfer message cell based on the provided example. +;; 2. Call recv_internal with this message. +;; 3. Assert that the debug_message is called and logs the correct information. +;; 4. (Optional) Assert any state changes in the contract if applicable (e.g., balance changes, event logs). + +;; --- Unit Test 2: Test jetton_notify handling --- +;; Description: Simulates receiving a jetton_notify message and checks if the contract processes it correctly. +;; Steps: +;; 1. Prepare a jetton_notify message cell based on the provided example. +;; 2. Call recv_internal with this message. +;; 3. Assert that the handle_jetton_notify function is called with the correct parameters. +;; 4. (Optional) Assert any side effects of handle_jetton_notify, such as sending internal messages. + +;; Example of how to prepare a message cell (Conceptual - FunC syntax): +;; cell jetton_internal_transfer_message = begin_cell() +;; .store_uint(jetton_internal_transfer, 32) +;; .store_uint(0, 64) ;; query_id +;; .store_coins(1000000000000000) ;; amount +;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; from +;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; response_address +;; .store_coins(100) ;; forward_ton_amount +;; .store_ref(begin_cell().end_cell()) ;; forward_payload (empty in this example) +;; .end_cell(); + +;; cell jetton_notify_message = begin_cell() +;; .store_uint(JETTON_NOTIFY_OPCODE, 32) +;; .store_uint(0, 64) ;; query_id +;; .store_coins(1000000000000000) ;; amount +;; .store_msg_addr("0:fbbc9fd45bbcc702993ea44c256d18d6e63cf7cfeda97918e0456075389ab38c") ;; sender +;; .store_ref(begin_cell() ;; forward_payload +;; .store_uint(0x00, 8) ;; sum_type: TextComment +;; .store_uint(0, 32) ;; op_code: 0 +;; .store_string_tail("🎉 Redeeming tokens...") ;; text +;; .end_cell()) +;; .end_cell(); \ No newline at end of file



op code:

const OP_TRANSFER = 0xf8a7ea5; const OP_TRANSFER_NOTIFICATION = 0x7362d09c; const OP_INTERNAL_TRANSFER = 0x178d4519; const OP_EXCESSES = 0xd53276db; ;;excesses const OP_BURN = 0x595f07bc; const OP_BURN_NOTIFICAITON = 0x7bdd97de; ;; TODO OPPS should be more unique or future on chain indexing const OP_MINT = 21; const OP_CODE_UPGRADE = 26; const OP_PLAY_JETTON = 31; const OP_PLAY_TON = 32; const OP_WITHDRAW_TON = 50; const OP_WITHDRAW_JETTON = 51; ;; Error Code const ERROR::WRONG_JETTON_SENDER_ADDRESS = 74; const ERROR::INSFUCIENT_FUNDS = 600; const ERROR::ZERO_RESERVES = 601; const ERROR::NULL_JETTON_WALLET = 602; const ERROR::MSG_VALUE_INSUFFICIENT = 603; const ERROR::WRONG_JETTON_WALLET = 604; const ERROR::SWAP_TON_NO_GAS = 605; const ERROR::QUOTE_BAD_AMOUNT = 606; const ERROR::QUOTE_BAD_RESERVES = 607; const ERROR::WRONG_RUG_PULL_ADDRESS = 608; ;; Play Jetton Amount const ERROR::WRONG_MIN_TON_AMOUNT = 700; const ERROR::WRONG_MAX_TON_AMOUNT = 701; const ERROR::WRONG_MIN_JETTON_AMOUNT = 702; const ERROR::WRONG_MAX_JETTON_AMOUNT = 703; const ERROR::WRONG_INSUFFICIENT_TON_AMOUNT = 704; const ERROR::WRONG_ADMIN_ADDRESS = 710; const ERROR::UNAUTHORIZED_DEPOSIT_REQUEST = 720; ;; Set Parameter const OP_SET_TOKEN_WAL
LET = 40; const OP_SET_AVAILABLE_WIN = 41; ;; Transfer Ownership const OP_TRANSFER_OWNERSHIP

✅️👍solidity version 

```pragma ton-solidity >= 0.40.3;
import "stdlib.fc";
import "op-codes.fc";
import "workchain.fc";
import "jetton-utils.fc";
import "gas.fc";
// Define data structures
storage#_ total_supply:Coins admin_address:MsgAddress next_admin_address:MsgAddress jetton_wallet_code:^Cell metadata_uri:^Cell = Storage;
(int, slice, slice, cell, cell) load_data() inline {
    slice ds = get_data().begin_parse();
    var data = (
        ds.load_coins(),  // total_supply        ds.load_msg_addr(),  // admin_address        ds.load_msg_addr(),  // next_admin_address        ds.load_ref(),  // jetton_wallet_code        ds.load_ref()  // metadata_uri    );
    ds.end_parse();
    return data;
}
() save_data(
    int total_supply,
    slice admin_address,
    slice next_admin_address,
    cell jetton_wallet_code,
    cell metadata_uri
) impure inline {
    set_data(
        begin_cell()
        .store_coins(total_supply)
        .store_slice(admin_address)
        .store_slice(next_admin_address)
        .store_ref(jetton_wallet_code)
        .store_ref(metadata_uri)
        .end_cell()
    );
}
// Initial values
() initialize() impure {
    int total_supply = 545217356060974508816;  // Total Supply    slice admin_address = parse_std_address("0:afc49cb8786f21c87045b19ede78fc6b46c51048513f8e9a6d44060199c1bf0c");  // Admin Address    slice next_admin_address = parse_std_address("0:4818f679ede118884806590b9b705a00fa6aa0cf7009d4b3d128ff263b031c88");  // Next Admin Address    cell jetton_wallet_code = load_jetton_wallet_code();  // Jwtton Wallet Code    cell metadata_uri = build_content_cell("https://cdn.dogs.dev/dogs.json
");  // Metadata    save_data(
        total_supply,
        admin_address,
        next_admin_address,
        jetton_wallet_code,
        metadata_uri    );
}
() send_to_jetton_wallet(
    slice to_address,
    cell jetton_wallet_code,
    int ton_amount,
    cell master_msg,
    int need_state_init
) impure inline {
    raw_reserve(ONE_TON / 100, RESERVE_REGULAR);  // Reserve for storage costs    cell state_init = calculate_jetton_wallet_state_init(
        to_address,
        my_address(),
        jetton_wallet_code    );
    slice to_wallet_address = calculate_jetton_wallet_address(state_init);
    // Create message    var msg = begin_cell()
    .store_msg_flags_and_address_none(BOUNCEABLE)
    .store_slice(to_wallet_address)  // Destination    .store_coins(ton_amount);
    if (need_state_init) {
        msg = msg.store_statinit_ref_and_body_ref(state_init, master_msg);
    } else {
        msg = msg.store_only_body_ref(master_msg);
    }
    send_raw_message(
        msg.end_cell(),
        SEND_MODE_PAY_FEES_SEPARATELY | SEND_MODE_BOUNCE_ON_ACTION_FAIL    );
}
() recv_internal(int msg_value, cell in_msg_full, slice in_msg_body) impure {
    slice in_msg_full_slice = in_msg_full.begin_parse();
    int msg_flags = in_msg_full_slice.load_msg_flags();
    if (is_bounced(msg_flags)) {
        in_msg_body.skip_bounced_prefix();
        // Process only bounced transfers (mint)
        if (!(in_msg_body.load_op() == op::internal_transfer)) {
            return ();
        }
        in_msg_body.skip_query_id();
        int jetton_amount = in_msg_body.load_coins();
        (int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri) = load_data();
        save_data(
            total_supply - jetton_amount,
            admin_address,
            next_admin_address,
            jetton_wallet_code,
            metadata_uri        );
        return ();
    }
    slice sender_address = in_msg_full_slice.load_msg_addr();
    int fwd_fee_from_in_msg = in_msg_full_slice.retrieve_fwd_fee();
    int fwd_fee = get_original_fwd_fee(
        MY_WORKCHAIN,
        fwd_fee_from_in_msg    );  // Estimate message forwarding costs    (int op, int query_id) = in_msg_body.load_op_and_query_id();
    (int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri) = load_data();
    if (op == op::mint) {
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, admin_address)
        );
        slice to_address = in_msg_body.load_msg_addr();
        check_same_workchain(to_address);
        int ton_amount = in_msg_body.load_coins();
        cell master_msg = in_msg_body.load_ref();
        in_msg_body.end_parse();
        // Check internal transfer message        slice master_msg_slice = master_msg.begin_parse();
        throw_unless(
            error::invalid_op,
            master_msg_slice.load_op() == op::internal_transfer        );
        master_msg_slice.skip_query_id();
        int jetton_amount = master_msg_slice.load_coins();
        master_msg_slice.load_msg_addr();  // from_address        master_msg_slice.load_msg_addr();  // response_address        int forward_ton_amount = master_msg_slice.load_coins();  // forward_ton_amount        check_either_forward_payload(master_msg_slice);  // Check payload        // Check enough amount for transfer        check_amount_is_enough_to_transfer(
            ton_amount,
            forward_ton_amount,
            fwd_fee        );
        send_to_jetton_wallet(
            to_address,
            jetton_wallet_code,
            ton_amount,
            master_msg,
            TRUE        );
        save_data(
            total_supply + jetton_amount,
            admin_address,
            next_admin_address,
            jetton_wallet_code,
            metadata_uri        );
        return ();
    }
    if (op == op::burn_notification) {
        // Process burn notification        int jetton_amount = in_msg_body.load_coins();
        slice from_address = in_msg_body.load_msg_addr();
        throw_unless(
            error::not_valid_wallet,
            equal_slices_bits(
                calculate_user_jetton_wallet_address(
                    from_address,
                    my_address(),
                    jetton_wallet_code                ),
                sender_address            )
        );
        save_data(
            total_supply - jetton_amount,
            admin_address,
            next_admin_address,
            jetton_wallet_code,
            metadata_uri        );
        slice response_address = in_msg_body.load_msg_addr();
        in_msg_body.end_parse();
        if (!is_address_none(response_address)) {
            // Create response message            var msg = begin_cell()
            .store_msg_flags_and_address_none(NON_BOUNCEABLE)
            .store_slice(response_address)  // Destination            .store_coins(0)
            .store_prefix_only_body()
            .store_op(op::excesses)
            .store_query_id(query_id);
            send_raw_message(
                msg.end_cell(),
                SEND_MODE_IGNORE_ERRORS | SEND_MODE_CARRY_ALL_REMAINING_MESSAGE_VALUE            );
        }
        return ();
    }
    if (op == op::provide_wallet_address) {
        // Provide wallet address        slice owner_address = in_msg_body.load_msg_addr();
        int include_address? = in_msg_body.load_bool();
        in_msg_body.end_parse();
        cell included_address = include_address?
            ? begin_cell().store_slice(owner_address).end_cell()
            : null();
        // Create response message        var msg = begin_cell()
        .store_msg_flags_and_address_none(NON_BOUNCEABLE)
        .store_slice(sender_address)
        .store_coins(0)
        .store_prefix_only_body()
        .store_op(op::take_wallet_address)
        .store_query_id(query_id);
        if (is_same_workchain(owner_address)) {
            msg = msg.store_slice(
                calculate_user_jetton_wallet_address(
                    owner_address,
                    my_address(),
                    jetton_wallet_code                )
            );
        } else {
            msg = msg.store_address_none();
        }
        cell msg_cell = msg.store_maybe_ref(included_address).end_cell();
        send_raw_message(
            msg_cell,
            SEND_MODE_CARRY_ALL_REMAINING_MESSAGE_VALUE | SEND_MODE_BOUNCE_ON_ACTION_FAIL        );
        return ();
    }
    if (op == op::change_admin) {
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, admin_address)
        );
        next_admin_address = in_msg_body.load_msg_addr();
        in_msg_body.end_parse();
        save_data(
            total_supply,
            admin_address,
            next_admin_address,
            jetton_wallet_code,
            metadata_uri        );
        return ();
    }
    if (op == op::claim_admin) {
        in_msg_body.end_parse();
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, next_admin_address)
        );
        save_data(
            total_supply,
            next_admin_address,
            address_none(),
            jetton_wallet_code,
            metadata_uri        );
        return ();
    }
    if (op == op::drop_admin) {
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, admin_address)
        );
        in_msg_body.end_parse();
        save_data(
            total_supply,
            address_none(),
            address_none(),
            jetton_wallet_code,
            metadata_uri        );
        return ();
    }
    if (op == op::change_metadata_uri) {
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, admin_address)
        );
        save_data(
            total_supply,
            admin_address,
            next_admin_address,
            jetton_wallet_code,
            begin_cell().store_slice(in_msg_body).end_cell()
        );
        return ();
    }
    if (op == op::upgrade) {
        throw_unless(
            error::not_owner,
            equal_slices_bits(sender_address, admin_address)
        );
        (cell new_data, cell new_code) = (
            in_msg_body.load_ref(),
            in_msg_body.load_ref()
        );
        in_msg_body.end_parse();
        set_data(new_data);
        set_code(new_code);
        return ();
    }
    if (op == op::top_up) {
        return ();  // Only accept TONs    }
    throw(error::wrong_op);
}
cell build_content_cell(slice metadata_uri) inline {
    cell content_dict = new_dict();
    content_dict.set_token_snake_metadata_entry("uri"H, metadata_uri);
    content_dict.set_token_snake_metadata_entry("decimals"H, "9");
    return create_token_onchain_metadata(content_dict);
}
(int, int, slice, cell, cell) get_jetton_data() method_id {
    (int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri) = load_data();
    return (
        total_supply,
        TRUE,
        admin_address,
        build_content_cell(metadata_uri.begin_parse()),
        jetton_wallet_code    );
}
slice get_wallet_address(slice owner_address) method_id {
    (int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri) = load_data();
    return calculate_user_jetton_wallet_address(
        owner_address,
        my_address(),
        jetton_wallet_code    );
}
slice get_next_admin_address() method_id {
    (int total_supply, slice admin_address, slice next_admin_address, cell jetton_wallet_code, cell metadata_uri) = load_data();
    return next_admin_address;
}


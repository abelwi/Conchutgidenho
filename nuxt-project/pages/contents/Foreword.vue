<template>
  <div class="h-screen flex flex-col items-center justify-center text-center bg-[#FFE8B9] relative px-6">
    <h2 class="text-5xl font-serif mb-6">Lời nói đầu</h2>
    <p class="text-lg font-serif text-left px-52 scroll-my-9">
      Mình 2k3 và mình không giống như hầu hết các bạn cùng trang lứa là theo hết 4 năm đại học.
      Mình chọn bỏ đại học sau 1 học kỳ. À thì trước đây mình học chuyên ngành Sinh học ở trường Đại
      học Khoa học Tự nhiên TP Hồ Chí Minh.
      <br>
      <br>
      Lý do mà mình quyết định bỏ học đại học là bởi mình thấy ‘chán'.
      Mình nhận ra mình không thích ngành mình đang học chút nào, chỉ trong một học kỳ, mình phải tiếp nhận
      những kiến thức mà não mình không thích ứng được, mình bị căng thẳng vì không biết mình đang làm cái 
      quái gì trong suốt thời gian ấy. Và rồi, mình quyết định bỏ đại học, may mắn thay vì mình có anh trai ủng hộ 
      và hỗ trợ mình hết sức nên mình tự tin hơn.  
      <br>
      <br>
      Nếu mà cậu thắc mặc liệu mình có bao giờ thấy hối hận khi bỏ đại học không? Thì mình sẽ trả lời thẳng với 
      cậu là ‘Không' - mình đến hiện tại, thực sự chưa từng hối hận vì quyết định đó, mình còn cảm thấy may mắn
      và cảm ơn bản thân đã cho mình cơ hội được nắm lấy những trải nghiệm thực tế mà chưa chắc các bạn đồng 
      trang lứa của mình có được. Mình của hiện tại, đã thực sự được ‘sống' từng ngày!
      <br>
      <br>
      Mình là một đứa rất nhạy cảm, hồi trước ở nhà mình khóc nhè nhiều lắm, động tí là mình cũng có thể khóc được. 
      Mình còn từng nghĩ mình mà đi làm diễn viên đóng cảnh khóc chắc cũng được ấy :)) Mình cũng hay nghĩ nhiều
      nữa, người ta gọi là overthinking á @@ Không biết nói mọi người tin không chứ mình của bây giờ bớt ‘cảm xúc' hơn
      của mình ngày trước nhiều lắm á! 
      <br>
      <br>
      Mình thì thích đàn guitar và thích hát, nhưng mình thích đàn hát cho một mình mình nghe nhất, còn không thì đàn
      hát cho một nhóm 5 người trở xuống thôi! Vì như vậy mình mới cảm thấy thoải mái và có thể giao tiếp với mọi người
      dễ dàng hơn và mình còn rất sợ đứng trước đám đông, mình bị căng thẳng tay chân run rẩy sẽ chẳng làm ăn được gì...
      <br>
      <br>
      Đó là sơ sơ về mình^^ có thể cậu đã biết hoặc chưa! Chúc cậu một ngày tốt lành nhé! ^^ 
    </p>

    <button
      @click="$emit('close')"
      class="absolute top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
  </div>
</template>

<script setup>
defineEmits(['close'])
</script>

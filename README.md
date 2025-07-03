<!DOCTYPE HTML>
<html lang="ko">
<머리>
 <meta charset=>UTF-8">
 <title>자리 뽑기 사이트</title>
 <스타일>
 .grid { 디스플레이: 그리드; 그리드-template-columns: 반복(7, 1fr); 간격: 10 px; 최대 너비: 500 px; 여백: 20 px 오토; }
 .cell {패딩}: 20 px; 텍스트 align: 가운데; 배경: #f0f0; 경계: 1 px 솔리드 #cccc; 글꼴 크기: 18 px; 커서: 포인터; }
 .cell.clicked {배경: #ffcccc; }
 </스타일>
</머리>
<바디>
 <h2 스타일="text-align:center;">자리 뽑기</h2>
 <div style="text-align:center; 여백 하단:10 px;">
 시작 번호: <입력 유형="number" ID="startNum" 값="1">
 끝 번호: <입력 유형="number" id="endNum" 값="28">
 제외할 번호(쉼표로): <input type="text" id="excludeNums" 자리 표시자="예: 3,5,12">
 <버튼 클릭="generateGrid()">자리 생성</버튼>
 </div>
 <div class="grid" id="seatGrid"></div>
 <스크립트>
 함수 셔플(어레이) {
 (i = array.length - 1, i > 0, i--) {에 대해
 const j = Math.floor (Math.random() * (i + 1));
 [array[i], array[j] = [array[j], array[i]];
 }
 }
 함수 generateGrid() {
 const grid = document.getElementById("시트그리드");
 그리드.innerHTML = "";
 = parseInt(document.getElementById("startNum")을 시작합니다.가치);
 = parseInt(document.getElementById("endNum")을 종료합니다.가치);
 = document.getElementById("excludeNums").value.split("",").map(s => parseInt(s.trim().filter(n =>!isNaN(n));
 만약 (시작 >= 종료 || 시작 < 1 || 종료 < 1) {알림 ("시작과 끝 번호를 정확히 입력해주세요}; 반환; }
 숫자 = [];
 (i = 시작; i <= 끝; i++) { if (!exclude.includes(i)) 숫자의 경우. push(i); }
 totalSeats = 끝 - 시작 + 1;
 blankNeed = totalSeats - number.length;
 모든 항목 = [...numbers];
 (i = 0; i < blanksNeed; i++) allItems.push("")에 대해;
 셔플(모든 항목);
 모든 항목.각 항목(num => {
 const div = document.createElement("div");
 div.className = "cell";
 div.textContent = num === "?" : num;
 div.addEventListener("클릭", () => {
 만약 (!div.classList.contains("클릭") {
 div.textContent = "×";
 div.classList.add("클릭됨");
 }
 });
 grid.appendChild(div);
 });
 }
 </script>
</body>
</html>

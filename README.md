'timescale 1ns / 1ps

module AND {
  input a,
  input b,
  output y
);
  assign y = a & b;
endmodule


module AND_tb

// 입력 및 출력 신호 선언
reg a;
reg b;
wire y;

// 테스트 대상 모듈 인스턴스화
AND instance_and (
  .a(a)
  .b(b)
  .y(y)
);
initial begin
  //초기 입력값 설정
  a=0; b=0;
  #10;  //10ns 대기
  a=0; b=1;
  #10;  //10ns 대기
  a=1; b=0;
  #10;  //10ns 대기
  a=1; b=1;
  #10;  //10ns 대기

  // 시뮬레이션 종료
  $finish;
end
//결과 모니터링
initial begin
  $monitor("시간=%t, 입력 a=%b, 출력 y=%b",$time,a,b,y);
  end
  endmodule
  

# ADDER
gate level modelling in Verilog
    module fulladder(input a,b,cin,
                 output sum,cout);
  wire w1,w2,w3;
  xor x1(w1,a,b);//sum
  xor x2(sum,w1,cin);
  and a1(w2,a,b);
  and a2(w3,w1,cin);
  or  m1(cout,w2,w3);
  
endmodule
  module tb;
  reg a,b,cin;
  wire sum,cout;
  fulladder m1(a,b,cin,sum,cout);
  initial begin 
    a=0;b=0;cin=0;#5;
    a=0;b=0;cin=1;#5;
    a=0;b=1;cin=0;#5;
    a=0;b=1;cin=1;#5;
    a=1;b=0;cin=0;#5;
    a=1;b=0;cin=1;#5;
    a=1;b=1;cin=0;#5;
    a=1;b=1;cin=1;#5;
  end
  initial $monitor("a=%d,b=%d,cin=%d,sum=%d,cout=%d",a,b,cin,sum,cout);
endmodule

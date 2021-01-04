# basic_gates
module basic_gates(input a, input b, output [6:0] y);
  and g1(y[0], a, b);
  or g2(y[1], a, b);
  not g3(y[2], a);
  nand g4(y[3], a, b);
  nor g5(y[4], a, b);
  xor g6(y[5], a, b);
  xnor g7(y[6], a, b);
endmodule
module test_basic_gates();
  wire [6:0] y;
  reg a,b;
  basic_gates bg1(a, b, y);
  initial begin
    a = 1'b0;
    b = 1'b1;
  end
  initial begin
    $display("a\tb\ty(and)\ty(or)\ty(not)\ty(nand)\ty(nor)\ty(xor)\ty(xnor)");
    $monitor("%b\t%b\t%b\t%b\t%b\t%b\t%b\t%b\t%b", a, b, y[0], y[1], y[2], y[3], y[4], y[5], y[6]);
    #10 a = 1'b0;
    b = 1'b0;
    #10 a=1'b0;
    b=1'b1;
    #10 a=1'b1;
    b=1'b0;
    #10 a=1'b1;
    b=1'b1;
  end
  initial begin
    //$dumpfile("basic_gates.dump");
    $dumpvars(1, test_basic_gates);
  end
endmodule
    
    
    
    
    
    
    

# Designing-a-4-bit-ALU-capable-of-performing-4-different-arithmetic-operations-
#Quartus|Verilog HDL


module test2(Opcode,Operand1,Operand2,Result,flagC,flagZ,flagS);    

input [2:0]  Opcode;

input [3:0]  Operand1,

             Operand2;

     

output reg [7:0] Result = 8'b0;

output reg  flagC = 1'b0,

            flagZ = 1'b0,
            
            flagS= 1'b0; 

parameter  [2:0] ADD = 3'b010,
                 SUB = 3'b100,
                 XOR = 3'b001,
                 XNOR = 3'b011;
      

always @ (Opcode or Operand1 or Operand2)

begin

 case (Opcode)

 ADD: begin

   Result = Operand1 + Operand2;

   flagC  = Result[4];

   flagZ  = (Result == 8'b0);
   
   flagS = Result[3];

  end

 SUB: begin

   Result = Operand1 - Operand2;

   flagC  = Result[4];

   flagZ  = (Result == 4'b0);
   flagS = Result[3];

  end

 

 XOR: begin

   Result = Operand1 ^ Operand2;

   flagZ  = (Result == 8'b0);

  end

 default: begin

   Result = 8'b0;

   flagC  = 1'b0;

   flagZ  = 1'b0;
   flagS  = 1'b0;

  end

 endcase

end

endmodule 






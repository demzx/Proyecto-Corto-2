module reset_sistem(
input wire [7:0] key,
output reg reset
    );
	 
always@*
       begin
       reset =1'b0;
		 case(key)
		 8'h2D : reset = 1; // Se deja pasar la tecla R
       default : reset = 0;
		 endcase
		 end
endmodule

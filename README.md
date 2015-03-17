# Proyecto-Corto-2
modulos que conforman el proyecto corto numero 2
//////////////////////////////////////////////////////////////////////////////////
// Company: Tecnologico de costa Rica
// Engineer: Edgar Gutierrez Leiva Oscar Soto Rivera 
// 
// Create Date:    20:16:45 03/14/2015 
// Design Name:    modulo principal 
// Module Name:    test_teclado 
// Project Name: Teclado_PS2
// Target Devices: 
// Tool versions: 
// Description: 
//
// Dependencies: 
//
// Revision: 
// Revision 0.01 - File Created
// Additional Comments: 
//
//////////////////////////////////////////////////////////////////////////////////
module test_teclado(
input wire Clock_in, Reset_in,//optem,
input wire ps2d_in, ps2c_in, rx_enable_in,
output wire b,carga,datod,
output wire [6:0] temp

    );

wire [7:0] tecla,tecla_T,dato_tec;
wire P,T,Listo_T,Enable_OP,Enable_modulos;


Modulo_Recepcion_PS2 PS2 (.Clock(Clock_in),.Reset(Reset_in), .ps2d(ps2d_in),.ps2c(ps2c_in),.rx_enable(rx_enable_in), .rx_done_Tick(data_ready),.breg_0(b),.dout(tecla));

capturar captu (.dout_1(tecla), .clck(Clock_in), .rst(Reset_in), .rx_done_tick_1(data_ready), .salida_1(tecla_T));

Disciriminador_de_teclas discriminador (.Tecla(tecla_T),.Tecla_sig(dato_tec));

maquina_de_Estados Maquina_control_Ps2 (
    .P(P), 
    .T(T), 
    .Clock(Clock_in), 
    .Reset(Reset_in), 
    .Listo_T(Listo_T), 
    .Enable_OP(Enable_OP), 
    .Enable_modulos(Enable_modulos)
    );







endmodule

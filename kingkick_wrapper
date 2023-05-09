`timescale 1ns / 1ps
module kingkick_wrapper( 
	input clk,
	input signed [10:0] sprite_x, //player
	input signed [10:0] sprite_y,
	input [9:0] x, //beam
	input [9:0] y,
	output [11:0]rgb,
	output sprite_on);

	
	localparam WIDTH = 146;
	localparam HEIGHT = 140;

	localparam ROWWIDTH = 7;
	localparam COLWIDTH = 7;


	reg [ROWWIDTH:0]row;
	reg [COLWIDTH:0]col;


	reg signed [10:0]x_signed,y_signed;

	
	assign sprite_on = (x_signed - sprite_x < WIDTH && y_signed - sprite_y < HEIGHT && x_signed - sprite_x > 0 && y_signed - sprite_y > 0) ? 1 : 0;
	always @(posedge clk) begin

		x_signed <= {1'b0,x};
		y_signed <= {1'b0,y};

		if (sprite_on) begin
			row <=y_signed-sprite_y;
			col <=x_signed-sprite_x;
		end
	end

	kingkick_rom kingkicker(.clk(clk),.row(row),.col(col),.color_data(rgb));

endmodule


library ieee;
use ieee.std_logic_1164.all;

entity Contador is
  port (Mode: in std_logic;
        CLK : in std_logic;
        UP   : out std_logic_vector(7 downto 0);
        DOWN : out std_logic_vector(7 downto 0));
end entity;

architecture arch of Contador is
  component UPDOWN is
    port (Mode: in std_logic;
          CLK : in std_logic;
          RES : in std_logic;
          En:   in std_logic;
          Qdo   : out std_logic_vector (3 downto 0);
          Qup     : out std_logic_vector (3 downto 0));
  end component;

  signal andEn1 : std_logic;
  signal andEn2 : std_logic;
  signal Qd    : std_logic_vector(7 downto 0);
  signal Qu    : std_logic_vector(7 downto 0);
  signal Qen   : std_logic;
  signal ign   : std_logic;
  signal notAnden1: std_logic;
  begin
    andEn1 <= Qu(1) and Qu(3);
    andEn2 <= Qu(5) and Qu(7);
    notAnden1 <= not andEn1;

    C1: UPDOWN   port map (Mode,
                                CLK,
                                andEn1,
                                notAnden1,
                                Qd(3 downto 0),
                                Qu(3 downto 0));
    C2: UPDOWN   port map (Mode, CLK, andEn2, andEn1, Qd(7 downto 4), Qu(7 downto 4));

    UP   <= Qu;
    DOWN <= Qd;
end arch;

# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: birousse <birousse@student.42.fr>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2013/09/25 08:56:14 by birousse          #+#    #+#              #
#    Updated: 2014/04/29 14:24:29 by birousse         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

LIBNAME	= ft_printf
NAME	= lib$(LIBNAME).a

LEVELS	= echo "../"; i+=1;
LEVELS	:= $(shell i=1; while [[ $$i -le $(MAKELEVEL) ]]; do $(LEVELS) done)

FILES	= ft_printf ft_printf_fd ft_printf_arg ft_get_v_arg ft_pf_c ft_pf_d \
		ft_pf_f ft_pf_s ft_pf_x
SRC		= $(addsuffix .c, $(FILES))
OBJ		= $(patsubst %.c,objs/%.o,$(SRC))

FTFLAGS	= $(patsubst %,-L%,$(DIR)) $(patsubst %,-l%,$(LNAME))
CFLAGS	= -Wall -Wextra -Werror -pedantic -I./$(LEVELS)includes

COLOR0	= \033[0m
COLOR1	= \033[32m
COLOR2	= \033[1;34m
COLOR3	= \033[31m
COLOR4	= \033[1;34m
COLOR5	= \033[1;30m
COLOR6	= \033[33m

PUCE1	= $(COLOR5) ¤
PUCE2	= $(COLOR5) -> $(COLOR6)
F_INFOS = \
	echo "$(PUCE2)binaire     : $(COLOR0)$(NAME)"; \
	echo "$(PUCE2)compilateur : $(COLOR0)$(CC)"; \
	echo "$(PUCE2)extra-flags : $(COLOR0)$(CFLAGS)";

ifdef DEBUG
    CFLAGS	+= -g
else
    CFLAGS	+= -O3
endif

all: $(NAME)

$(NAME): $(OBJ)
	@if [ "$($_INFOS)" != "OK" ]; then $(call F_INFOS) $(eval $_INFOS :=OK) fi;
	@echo "$(PUCE1)$(COLOR1) Compilation de la librairie !$(COLOR0)"
	@ar rc $(NAME) $(OBJ)
	@ranlib $(NAME)

objs/%.o: srcs/$(notdir %.c)
	@if [ "$($_INFOS)" != "OK" ]; then $(call F_INFOS) $(eval $_INFOS :=OK) fi;
	@mkdir -p objs
	@$(CC) -c $(CFLAGS) -o "$@" "$<"

clean:
	@if [ "$($_INFOS)" != "OK" ]; then $(call F_INFOS) $(eval $_INFOS :=OK) fi;
	@$(RM) $(OBJ)
	@$(RM) -r objs

fclean: clean
	@test -f "$(NAME)" \
		&& echo "$(PUCE1)$(COLOR3) Suppression de la librairie !$(COLOR0)" \
		&& $(RM) $(NAME) || echo "\c";

re: fclean all

.PHONY: all clean fclean re

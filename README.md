# pipe_aaaformaxxxxx

#include<erno.h>
#include<signal.h>
void it_sigpipe()
{
printf("Réception du signal SIGPIPE\n") ;
}
main()
{
int p_desc[2] ;
signal(SIGPIPE,it_sigpipe) ;
pipe(p_desc) ; /* création du tube */
close(p_desc[0]) ; /* fermeture du conduit en lecture */
if (write(p_desc[1],"0",1) == -1)
perror("Erreur write") ;
}

/* GUIA-GTK-FOR-MY-FRIENDS

***** 1° 
        Copie o código abaixo !!!!!!!!
	
	2° Cole ACIMA do seu main
	
	4° Inclua a biblioteca gtk/gtk.h/
	#include <gtk/gtk.h>

	3° Use as funcoes 
  
 */  
 
 
 
typedef struct _gtk_config {
	
	GtkBuilder *builder;
	GtkWindow *mainWindow;
	GtkButton *send;
	GtkComboBoxText *pin;
	GtkComboBoxText *io;	
	GtkSpinButton *delay;
	
} gtk_config;

gtk_config gtk;        

static void gtk_start_application(int argc, char **argv) {
	
	gtk_init (&argc, &argv);
		
	//Creating GtkBuilder object;
	gtk.builder = gtk_builder_new();
	gtk_builder_add_from_file(gtk.builder, "teste.xml", NULL);
	
	//Creating Window object;
	gtk.mainWindow = 
		(GtkWindow*)gtk_builder_get_object(gtk.builder,"window1");
	
	//Creating pin_select
	gtk.io = 
		(GtkComboBoxText*)gtk_builder_get_object(gtk.builder, "comboboxtext2");
	
	gtk.pin = 
		(GtkComboBoxText*)gtk_builder_get_object(gtk.builder, "comboboxtext1");
		
	//Creating send button;
	gtk.send =
		(GtkButton*)gtk_builder_get_object(gtk.builder, "button1");	

	//Creating spinButton;
	gtk.delay =
		(GtkSpinButton*)gtk_builder_get_object(gtk.builder, "spinbutton1");
	gtk_adjust_spin_button();	
	
	//Showing widgets;			
	gtk_widget_show((GtkWidget*)gtk.mainWindow);	
}

//Use a função para puxar o valor dos campos de entrada
//Basta chamar a função, passar o campo de entrada aonde está o valor que vcs querem
// Esta função retorna um double;

//Exemplo :
	//GtkEntry *sua_entrada = .... ( sua entrada vc quem puxa )
//	double numero = gtk_get_entry_value(sua_entrada); 	

double gtk_get_entry_value (GtkEntry* entry) {
	
	double value = atof(gtk_entry_get_text(entry)); 

	return value;
}

//Use essa funcao para escrever no label que vc quer imprimir o resultado

//Exemplo
//	gtk_escreve_no_label(

void gtk_escreve_no_label(double numero, GtkLabel* label) {

	char resultado[10];
	
	sprintf(resultado, %f, numero);
	
	gtk_label_set_text(label, resultado);

}

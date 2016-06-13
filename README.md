# GUIA-GTK-FOR-MY-FRIENDS

***** 1° 
        Copie o código abaixo !!!!!!!!
        
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

	//Initiate signal handler;
	gtk_signal_handler_init();	
}

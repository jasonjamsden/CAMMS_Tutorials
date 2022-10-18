# First Program

After booting Linux operational System to the STM32MP15 Microprocessor following the tutorial: **Boot-STM32MP15**, and completing the basic operation of the STM32MP15 Microprocessor with the following tutorial: **Execute-basic-Commands** it’s time to write our first own program which from the **host** computer will execute a basic print operation in the  Microprocessor.

# Step 1: Host computer configuration and SDK Installation

- First you need to follow the previous tutorial: **SDK-stallation** and install the SDK to the host computer.

# Step 2:

- Create a directory that will host your source codes:

`$> mkdir ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/stm32mp1-openstlinux-22.06.15`
`$> mkdir ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/stm32mp1-openstlinux-22.06.15/sources`

- Create a directory that will host your source codes

`$> mkdir ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/stm32mp1-openstlinux-22.06.15/sources/gtk_hello_world_example`
`$> cd ~/STM32MPU_workspace/STM32MP1-Ecosystem-v4.0.0/Developer-Package/stm32mp1-openstlinux-22.06.15/sources/gtk_hello_world_example`

- Create the source code file for your user space example: **gtk_hello_world.c**:

```
#include <gtk/gtk.h>

static void
print_hello (GtkWidget *widget,
             gpointer   data)
{
  g_print ("Hello World\n");
}

static void
activate (GtkApplication *app,
          gpointer        user_data)
{
  GtkWidget *window;
  GtkWidget *button;
  GtkWidget *button_box;

  window = gtk_application_window_new (app);
  gtk_window_set_title (GTK_WINDOW (window), "Window");
  gtk_window_set_default_size (GTK_WINDOW (window), 200, 200);

  button_box = gtk_button_box_new (GTK_ORIENTATION_HORIZONTAL);
  gtk_container_add (GTK_CONTAINER (window), button_box);

  button = gtk_button_new_with_label ("Hello World");
  g_signal_connect (button, "clicked", G_CALLBACK (print_hello), NULL);
  g_signal_connect_swapped (button, "clicked", G_CALLBACK (gtk_widget_destroy), window);
  gtk_container_add (GTK_CONTAINER (button_box), button);

  gtk_widget_show_all (window);
}
```




 

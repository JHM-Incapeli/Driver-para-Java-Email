
*******************************************************















-La contraseña de 16 digitos es generada por google al activar la verificación de dos pasos
	PASOS:
	1) Activar verificación de dos pasos
	2) La contraseña la podrás generar con un nuevo botón que aparece al
	   activar la verificación de dos pasos
	3) visualizas dos opciones contraseña para un dispositivo o aplicación(app) eliges app	
	4) Disfruta 


-Para enviar mensajes solo se necesita estas dos librerias
----javax.activation-1.1.0.v201105071233.jar
----mail.jar


        codigo: Solo para enviar mensaje

	    //de
        String correo = "Correo_que_envia_el_mensaje@gmail.com";
        String contra = "Contraseña de 16 digitos";
        
        
        /// para
        String destinatario = txtResive.getText();
        String Asunto = txtAsunto.getText();
        String contenido = txtConteneido.getText();

        try {
            Properties p = new Properties();
            p.put("mail.smtp.host", "smtp.gmail.com");
            p.setProperty("mail.smtp.starttls.enable", "true");
            p.put("mail.smtp.ssl.trust", "smtp.gmail.com");
            p.setProperty("mail.smtp.port", "587");
            p.setProperty("mail.smtp.user", correo);
            p.setProperty("mail.smtp.auth", "true");
            p.setProperty("mail.smtp.ssl.protocols", "TLSv1.2");
            
            Session s = Session.getDefaultInstance(p);
            MimeMessage mensaje = new MimeMessage(s);
            mensaje.setFrom(new InternetAddress(correo));
	    // la persona que recive el correo
            mensaje.addRecipient(Message.RecipientType.TO, new InternetAddress(destinatario));
            // Asunto del correo
	    mensaje.setSubject(Asunto);
	    // Conteneido del correo
            mensaje.setText(contenido);

            Transport t = s.getTransport("smtp");
            t.connect(correo, contra);
            t.sendMessage(mensaje, mensaje.getAllRecipients());
            t.close();
            JOptionPane.showMessageDialog(null, "Mensaje enviado");
        } catch (MessagingException e) {
            JOptionPane.showMessageDialog(null, "Error al enviar" + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }


        

                        ************************************************
                                //para enviar archivo adjunto
                        ************************************************   
                        ----javax.activation-1.1.0.v201105071233.jar
                        ----mail.jar
        ///// de
        String correo = "elyuscas6000@gmail.com";
        String contra = "oulclyooakumjlrk";
        
        /// para
        String destinatario = txtResive.getText();
        String Asunto = txtAsunto.getText();
        String contenido = txtConteneido.getText();
        try {
            JFileChooser abrir = new JFileChooser();
             int ceroOUno = abrir.showOpenDialog(null);
             File ruta= abrir.getSelectedFile();
             String fileName= abrir.getSelectedFile().getName();
            
            Properties p = new Properties();
              p.put("mail.smtp.host", "smtp.gmail.com");
              p.setProperty("mail.smtp.starttls.enable", "true");
              p.put("mail.smtp.ssl.trust", "smtp.gmail.com");
              p.setProperty("mail.smtp.port", "587");
              p.setProperty("mail.smtp.user", correo);
              p.setProperty("mail.smtp.auth", "true");
              p.setProperty("mail.smtp.ssl.protocols", "TLSv1.2");
            
            Session s = Session.getDefaultInstance(p);
            // para enviar enviar archivos adjuntos
            BodyPart texto = new MimeBodyPart();
            //El texto del mensaje lo enviaremos mediante este objeto
             texto.setText(contenido);
            BodyPart adjunto = new MimeBodyPart();
              adjunto.setDataHandler(new DataHandler(new FileDataSource(ruta)));
              adjunto.setFileName(fileName);
            
            MimeMultipart m = new MimeMultipart();
              m.addBodyPart(texto);
              m.addBodyPart(adjunto);
            
            //***********************************************
            
            MimeMessage mensaje = new MimeMessage(s);
              mensaje.setFrom(new InternetAddress(correo));
              mensaje.addRecipient(Message.RecipientType.TO, new InternetAddress(destinatario));
              mensaje.setSubject(Asunto);
              mensaje.setContent(m);
             /*
            Protocolo para tranferecnica cimple de email smtp
            */
            Transport t = s.getTransport("smtp");
             t.connect(correo, contra);
             t.sendMessage(mensaje, mensaje.getAllRecipients());
             t.close();
            JOptionPane.showMessageDialog(null, "Mensaje enviado");
            dispose();
        } catch (MessagingException e) {
            JOptionPane.showMessageDialog(null, "Error al enviar" + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }

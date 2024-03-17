# chandelier
private void nama() {

    // We stored the public class snake in the nama variable    

    Nama = JOptionPane.showInputDialog(this, "Please Input Your Name:");

    if (Nama == null) {

        System.exit(0);

    } else {

        if (Nama.equals("")) {

            JOptionPane.showMessageDialog(this, "Name Already Exist!");

            nama();

        } else {

            try {

                Connection c = ClassDB.getkoneksi();

                Statement st = (Statement) c.createStatement();

                String ceknama = "Select * from score where nama = '" + Nama.toString() + "'";

                ResultSet r = st.executeQuery(ceknama);

                if (r.next()) {

                    return;

                } else {

                    try {

                        st.executeUpdate("Insert into score(nama) values('" + Nama.toString() + "')");

                    } catch (Exception e) {

                        System.out.println(e);

                    }

                }



            } catch (Exception e) {

                System.out.println(e);

            }

        }

    }

}

# -how
namespace pj
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            // Initialize total
            int iTotal = 0;

            // Get and process coffee price and quantity if "coffee" is selected
            string strCoffeePrice = tbCoffeePrice.Text;
            string strCoffeeQuantity = tbCoffeeQuantity.Text;

            int iCoffeePrice = 0;
            int iCoffeeQuantity = 0;
            try
            {
                if (coffee.Checked)  // Check if the "coffee" option is selected
                {
                    iCoffeePrice = int.Parse(strCoffeePrice);
                    iCoffeeQuantity = int.Parse(strCoffeeQuantity);
                    // Calculate coffee total
                    iTotal += iCoffeePrice * iCoffeeQuantity;
                }
            }
            catch (Exception)
            {
                // Handle exceptions
                iCoffeePrice = 0;
                iCoffeeQuantity = 0;
            }

            // Get and process green coffee price and quantity if "green" is selected
            string greenCoffeePrice = tbGreenCoffeePrice.Text;
            string greenCoffeeQuantity = tbGreenCoffeeQuantity.Text;

            int iGreenCoffeePrice = 0;
            int iGreenCoffeeQuantity = 0;
            try
            {
                if (grr.Checked)  // Check if the "green coffee" option is selected
                {
                    iGreenCoffeePrice = int.Parse(greenCoffeePrice);
                    iGreenCoffeeQuantity = int.Parse(greenCoffeeQuantity);
                    // Calculate green coffee total
                    iTotal += iGreenCoffeePrice * iGreenCoffeeQuantity;
                }
            }
            catch (Exception)
            {
                // Handle exceptions
                iGreenCoffeePrice = 0;
                iGreenCoffeeQuantity = 0;
            }

            // Display the total in the TextBox
            tbTotal.Text = iTotal.ToString();

            // Calculate change
            string strCash = tbCash.Text; // Get cash input
            int iCash = 0;
            try
            {
                iCash = int.Parse(strCash);

                if (iCash >= iTotal)
                {
                    int iChange = iCash - iTotal;
                    tbChange.Text = iChange.ToString();

                    // Calculate denominations for change
                    int[] denominations = { 1000, 500, 100, 50, 20, 10, 5, 1 };
                    int remainingChange = iChange;

                    foreach (int denom in denominations)
                    {
                        int count = remainingChange / denom;
                        remainingChange %= denom;

                        // Display denomination count in corresponding TextBox
                        switch (denom)
                        {
                            case 1000:
                                tb1000.Text = count.ToString();
                                break;
                            case 500:
                                tb500.Text = count.ToString();
                                break;
                            case 100:
                                tb100.Text = count.ToString();
                                break;
                            case 50:
                                tb50.Text = count.ToString();
                                break;
                            case 20:
                                tb20.Text = count.ToString();
                                break;
                            case 10:
                                tb10.Text = count.ToString();
                                break;
                            case 5:
                                tb5.Text = count.ToString();
                                break;
                            case 1:
                                tb1.Text = count.ToString();
                                break;
                        }
                    }
                }
                else
                {
                    MessageBox.Show("เงินที่ได้รับไม่เพียงพอ");
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกจำนวนเงินที่ถูกต้อง");
            }
        }
    }
}

# repocoba
Aplikasi ini berfungsi untuk menghitung nilai tukar mata uang dari dollar ke rupiah.Pada aplikasi ini satu dollar senilai Rp.15.000
## Scope & Functionalities
- User dapat memasukan angka
- User dapat menyentuh tombol hitung
- User akan mendapatkan informasi"INVALID" jika memasukan huruf

## How does it works?
Pertama program akan mengeksekusi terlebih dahulu ,method dibawah ini:

      
      public MainWindow()
        {
            InitializeComponent();
            currencyController = new CurrencyController();
            
        }



Lalu pada private void Button_Hitung_Clik terdapat logic untuk menangani human error berupa kesalahan input.ketika user menginput angka maka terdapat info "INVALID".

    private void Button_Hitung_Click(object sender, RoutedEventArgs e)
        {
            var nominalInput = InputTextBox.Text;

            var result = "invalid";
            if (currencyController.isAllowed(nominalInput))
            {
                result = currencyController.usdToIdr(nominalInput);
            }
            resultLabel.Content = result;
      
        }


Untuk logika perhitungannya terdapat pada class CurrencyContrroller.s

 public string usdToIdr(string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 15000;
            return Convert.ToString(result);
        }
        

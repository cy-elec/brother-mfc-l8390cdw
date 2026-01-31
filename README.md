## Brother MFC-L8390CDW

### Installation

```bash
# Install with
makepkg -si
```

### Network

To change the printer to a network printer, find it's ip address and modify the printer on your cups server ([localhost:631](http://localhost:631/printers/MFCL8390CDW))
1. Select 'Internet Printing Protocol (ipps)'
1. Enter the correct connection (e.g. ipps://10.100.20.100/ipp/print)
1. Change Description and Location as desired
1. Select 'Or Provide a PPD File:', then navigate to '/opt/brother/Printers/mfcl8390cdw/cupswrapper/' and select the ppd (e.g. 'brother_mfcl8390cdw_printer_en.ppd')
1. Select 'Modify Printer' to finish setup


### Blurry Print

Ensure that the problem lies not within your initial viewer (e.g. gecko(firefox/thunderbird/...) renders blurry to prints)

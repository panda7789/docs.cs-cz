---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 98d264cb081af0c0ed96b7e439f93224608467d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717412"
---
# <a name="custom-binding-transport-and-encoding"></a>Kódování a přenos vlastní vazby
Seřazený seznam elementů diskrétní vazby je definován vlastní vazby. Tento příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenos a kódování prvků zprávy.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka je založena na [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md)a byla změněna konfigurace tři koncových bodech, které podporují přenosy HTTP, TCP a pojmenovaného kanálu u vlastních vazeb. Podobně změnil konfiguraci klienta a změněn kód klienta ke komunikaci s každým tři koncových bodů.  
  
 Vzorek ukazuje ke konfiguraci vlastních vazbu, která podporuje konkrétní přenos a kódování zprávy. Toho dosahuje tím, že nakonfigurujete přenos a kódování pro zprávu `binding` elementu. Řazení elementů vazby je důležité při definování vlastní vazby, protože každý reprezentuje vrstvu v kanálu zásobníku (viz [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md)). Tato vzorovým kódem se nakonfiguruje tři vlastních vazeb: přenos pomocí protokolu HTTP s kódování textu, přenosu protokolu TCP s kódování textu a pojmenovaný kanál přenosu pomocí binárního kódování.  
  
 Konfigurace služby definuje vlastní vazby následujícím způsobem:  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi jsou zobrazeny v okně konzoly služby a klienta. Klient komunikuje s jednotlivými tři koncové body, přístup k první HTTP a TCP a nakonec pojmenovaného kanálu. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
 `namedPipeTransport` Vazby nepodporuje operace machine-to-machine. Používá se pouze pro komunikaci ve stejném počítači. Při spuštění ukázky ve scénáři mezi počítači, okomentujte proto následující řádky do souboru kódu klienta:  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Viz také:

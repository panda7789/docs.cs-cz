---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145161"
---
# <a name="custom-binding-transport-and-encoding"></a>Kódování a přenos vlastní vazby
Vlastní vazba je definována seřazeným seznamem samostatných prvků vazby. Tato ukázka ukazuje, jak nakonfigurovat vlastní vazby s různými prvky přenosu a kódování zpráv.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka je založena na [vlastním hostiteli](../../../../docs/framework/wcf/samples/self-host.md)a byla upravena tak, aby nakonfigurovala tři koncové body pro podporu přenosů HTTP, TCP a NamedPipe s vlastními vazbami. Konfigurace klienta byla podobně upravena a kód klienta byl změněn tak, aby komunikoval s každým ze tří koncových bodů.  
  
 Ukázka ukazuje, jak nakonfigurovat vlastní vazbu, která podporuje konkrétní přenos a kódování zpráv. Toho lze dosáhnout konfigurací přenosu a kódování zprávy `binding` pro prvek. Řazení elementů vazby je důležité při definování vlastní vazby, protože každý představuje vrstvu v zásobníku kanálu (viz [Vlastní vazby).](../../../../docs/framework/wcf/extending/custom-bindings.md) Tato ukázka konfiguruje tři vlastní vazby: přenos HTTP s kódováním textu, přenos TCP s kódováním textu a přenos NamedPipe s binárním kódováním.  
  
 Konfigurace služby definuje vlastní vazby takto:  
  
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
  
 Při spuštění ukázky jsou zobrazeny požadavky na operaci a odpovědi v okně služby i klientské konzole. Klient komunikuje s každým ze tří koncových bodů, přístup první HTTP, pak TCP a nakonec NamedPipe. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
 Vazba `namedPipeTransport` nepodporuje operace mezi stroji. Používá se pouze pro komunikaci na stejném počítači. Proto při spuštění ukázky ve scénáři mezi počítači, komentář se následující řádky v souboru kódu klienta:  
  
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
> Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  

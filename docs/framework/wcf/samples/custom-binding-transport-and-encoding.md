---
title: "Kódování a přenos vlastní vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4e26e332cc67fc462c703c502594a8a36758501
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-binding-transport-and-encoding"></a>Kódování a přenos vlastní vazby
Vlastní vazby je definována seřazený seznam prvky diskrétní vazby. Tento příklad znázorňuje, jak nakonfigurovat vlastní vazby s různými přenosu a elementy kódování zprávy.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka je založena na [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md)a byla změněna konfigurace tři koncových bodů pro podporu protokolu HTTP, TCP a pojmenovaný kanál přenosy u vlastních vazeb. Podobně byla změněna konfigurace klienta a změnit kód klienta ke komunikaci s jednotlivými tři koncových bodů.  
  
 Ukázka předvádí nakonfigurovat vlastní vazby, která podporuje konkrétního přenosu a kódování zprávy. To se provádí konfigurace přenos a zprávy pro kódování `binding` elementu. Řazení elementů vazby je důležité k definování vlastní vazby, protože každý představuje vrstvy v zásobníku kanál (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Tato ukázka nakonfiguruje tři vlastní vazby: přenosového protokolu HTTP s kódování textu, přenos TCP s kódování textu a přenos pojmenovaný kanál s binárního kódování.  
  
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
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly služby a klienta. Klient komunikuje s jednotlivými tři koncové body, přístup k první protokolu HTTP, pak TCP a nakonec pojmenovaný kanál. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
 `namedPipeTransport` Vazba nepodporuje operace počítač počítače. Použije se pouze pro komunikaci ve stejném počítači. Proto při spuštění ukázky ve scénáři mezi počítači, komentář následující řádky do souboru kódu klienta:  
  
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
>  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Viz také

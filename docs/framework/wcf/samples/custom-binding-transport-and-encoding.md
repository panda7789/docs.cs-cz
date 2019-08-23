---
title: Kódování a přenos vlastní vazby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 83b6f98ca889d4f80841b629d7a958401bac1e87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953743"
---
# <a name="custom-binding-transport-and-encoding"></a>Kódování a přenos vlastní vazby
Vlastní vazba je definována seřazeným seznamem diskrétních prvků vazby. Tato ukázka předvádí, jak nakonfigurovat vlastní vazbu s různými typy přenosů a kódování zpráv.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka je založená na [vlastním hostiteli](../../../../docs/framework/wcf/samples/self-host.md)a byla upravena pro konfiguraci tří koncových bodů pro podporu přenosů http, TCP a pojmenovaný kanál s vlastními vazbami. Konfigurace klienta se obdobně změnila a kód klienta se změnil, aby komunikoval s každým ze tří koncových bodů.  
  
 Ukázka ukazuje, jak nakonfigurovat vlastní vazbu, která podporuje konkrétní přenos a kódování zpráv. To je provedeno konfigurací přenosu a kódováním zpráv pro `binding` element. Řazení elementů vazby je důležité při definování vlastní vazby, protože každá představuje vrstvu v zásobníku kanálů (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)). Tato ukázka konfiguruje tři vlastní vazby: přenos HTTP s kódováním textu, přenos TCP s kódováním textu a pojmenovaný kanál přenos s binárním kódováním.  
  
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
  
 Při spuštění ukázky se požadavky na operace a odpovědi zobrazují v okně konzoly služby i klienta. Klient komunikuje s každým ze tří koncových bodů, přistupuje k prvnímu HTTP, pak TCP a finally pojmenovaný kanál. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
 `namedPipeTransport` Vazba nepodporuje operace mezi počítačem a počítačem. Používá se pouze pro komunikaci ve stejném počítači. Proto při spuštění ukázky v případě více počítačů přidejte do souboru s klientským kódem následující řádky:  
  
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
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  

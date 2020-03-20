---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183343"
---
# <a name="srmp"></a>SRMP
Tato ukázka ukazuje, jak provádět transakční komunikaci ve frontě pomocí služby Řízení front zpráv (Služba MSMQ) přes protokol HTTP.  
  
 Ve frontové komunikaci klient komunikuje se službou pomocí fronty. Přesněji řečeno, klient odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.  
  
 Služba MSMQ umožňuje použití protokolu HTTP (včetně použití protokolu HTTPS) k odesílání zpráv do fronty. V tomto příkladu jsme demonstrovat pomocí Windows Communication Foundation (WCF) ve frontě komunikace a jak odesílat zprávy přes HTTP. Služba MSMQ používá protokol s názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Před spuštěním **ukázky v aplikaci Přidat nebo odebrat součásti systému Windows**zkontrolujte, zda je služba MSMQ nainstalována s podporou protokolu HTTP. Instalace podpory protokolu HTTP automaticky nainstaluje internetovou informační službu (IIS) a přidá podporu protokolu do služby IIS pro službu MSMQ.  
  
5. Chcete-li si být jisti, že se protokol HTTP používá pro komunikaci, můžete povolit spuštění služby MSMQ v režimu tvrzené. Tím je zajištěno, že žádné zprávy do fronty hostované v počítači může dorazit pomocí jakéhokoli přenosu bez protokolu HTTP.  
  
6. Po výběru služby MSMQ pro spuštění v režimu tvrzené technologie vyžaduje počítač opětovné spuštění v systému Windows Server 2003.  
  
7. Spusťte službu.  
  
8. Spusťte klienta. Ujistěte se, že změníte adresu koncového bodu tak, aby ukazovala na název počítače nebo ADRESU IP místo localhost. Klient odešle zprávu a ukončí.  
  
## <a name="requirements"></a>Požadavky  
 Chcete-li spustit tuto ukázku, musí být služba IIS nainstalována na službu i na klientských počítačích kromě služby MSMQ.  
  
## <a name="demonstrates"></a>Demonstruje  
 Ukázka ukazuje odesílání zpráv ve frontě WCF pomocí služby MSMQ přes protokol HTTP. To se také nazývá zasílání zpráv SRMP. Při odeslání zprávy ve frontě převede služba MSMQ v odesílajícím počítači zprávy do přijímajícího správce front prostřednictvím přenosu TCP nebo HTTP. Výběrem SRMP, uživatel označuje volbu PROTOKOLU HTTP jako přenos pro přenos fronty. SRMP Secure umožňuje použití protokolu HTTPS.  
  
## <a name="example"></a>Příklad  
 Ukázkový kód je založen na transakčním vzorku. Způsob odeslání zprávy do fronty a přijetí zprávy z fronty pomocí protokolu SRMP je stejný jako odesílání a přijímání zpráv pomocí nativního protokolu.  
  
 Konfigurace klienta je změněna tak, aby označovala volbu protokolu přenosu fronty. Protokol přenosu fronty může být jedním z nativní, SRMP nebo SrmpSecure. Ve výchozím nastavení je přenosový protokol nativní. Klient a služba zadat v konfiguraci pro použití SRMP v tomto příkladu.  
  
 Existují omezení SRMP ve vztahu k bezpečnosti dopravy. Výchozí zabezpečení přenosu služby MSMQ vyžaduje službu Active Directory, která vyžaduje, aby se správce fronty odesílání a správce přijímající fronty byli umístěni ve stejné doméně systému Windows. To není možné při odesílání zpráv přes hranice PROTOKOLU HTTP. Jako takové výchozí zabezpečení přenosu nefunguje. Zabezpečení přenosu musí být nastaveno na certifikát, pokud je požadováno zabezpečení přenosu. Zabezpečení zpráv lze také použít k zabezpečení zprávy. V této ukázce je vypnuto zabezpečení přenosu i zpráv pro ilustraci zasílání zpráv SRMP.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Spuštění ukázky dává následující výstup.  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  

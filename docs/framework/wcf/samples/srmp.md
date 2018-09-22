---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 62075cccfa8ff2c6a181d633756a5f9bc8969932
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581308"
---
# <a name="srmp"></a>SRMP
Tento příklad znázorňuje způsob provedení transakčního komunikaci ve frontě pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.  
  
 MSMQ – umožňuje použití protokolu HTTP (včetně použití protokolu HTTPS) pro odesílání zpráv do fronty. V tomto příkladu jsme ukazují, jak pomocí služby Windows Communication Foundation (WCF) zařazených do fronty komunikace a jak odesílat zprávy pomocí protokolu HTTP. Protokol volá SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP používaný službou MSMQ.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Před spuštěním ukázky **přidat nebo odebrat součásti Windows**, ujistěte se, že je služba MSMQ nainstalovaná s podporou protokolu HTTP. Podpora protokolu HTTP instalace automaticky nainstaluje Internetové informační služby (IIS) a přidává podporu protokolu ve službě IIS pro službu MSMQ.  
  
5.  Pokud chcete mít jistotu, že protokol HTTP se používá pro komunikaci, můžete povolit služby MSMQ pro spuštění v zesíleném režimu. Tím se zajistí, že žádné zprávy do fronty hostované na počítači můžou přijít pomocí jakékoli přenosu jiným protokolem než HTTP.  
  
6.  Po výběru služby MSMQ pro spuštění v zesíleném režimu, daný počítač vyžaduje restartování na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Spuštění služby.  
  
8.  Spustíte klienta. Ujistěte se, že změníte adresu koncového bodu tak, aby odkazoval na název počítače nebo IP adresu místo localhost. Klient odešle zprávu a ukončí.  
  
## <a name="requirements"></a>Požadavky  
 Chcete-li tuto ukázku spustit, musí být nainstalovaná služba IIS ve službě a klientské počítače kromě služby MSMQ.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vzorek ukazuje odesílání WCF přes protokol HTTP pomocí služby MSMQ zprávy zařazené do fronty. Označuje se také, SRMP zasílání zpráv. Zprávy ve frontě je odeslání, MSMQ na odesílání přenosů počítače zprávy, které využívá správce fronty přes protokol TCP nebo HTTP přenosu. Výběrem SRMP uživatele určuje řadu HTTP jako přenos pro přenos fronty. Zabezpečení SRMP umožňuje použití protokolu HTTPS.  
  
## <a name="example"></a>Příklad  
 Počet zrušených zpracovaných vzorku vychází ukázkový kód. Jak odeslat zprávu do fronty a přijímat zprávy z fronty pomocí SRMP je stejný jako odesílání a příjem zpráv pomocí nativního protokolu.  
  
 K označení výběru fronty přenosu protokolu dojde ke změně konfigurace pro klienta. Protokol fronty přenosu může být jedna z nativní, SRMP nebo SrmpSecure. Ve výchozím nastavení je přenos protokolu nativní. Klient a služba zadejte v konfiguraci použít SRMP v tomto příkladu.  
  
 Existují určitá omezení SRMP ve vztahu k zabezpečení přenosu. Zabezpečení přenosu služby MSMQ výchozí vyžaduje služby Active Directory, která vyžaduje, aby odesílající správce fronty a využívá správce fronty se nacházejí ve stejné doméně Windows. To není možné při odesílání zprávy přes hranice protokolu HTTP. Zabezpečení výchozího přenosu v důsledku toho nebude fungovat. Zabezpečení přenosu musí být nastavena na certifikát, pokud se vyžaduje zabezpečení přenosu. Zabezpečení zpráv lze použít také k zabezpečení zprávy. V této ukázce zabezpečení přenosu a zpráva je vypnuté, kvůli znázornění SRMP zasílání zpráv.  
  
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
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Spuštění ukázky provede následující výstup.  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a>Viz také

---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: f3b0e57f05ccb77eef25c97e7d5d028183e7b13e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600929"
---
# <a name="srmp"></a>SRMP
Tato ukázka předvádí, jak pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP provádět komunikaci v transakční frontě.  
  
 V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.  
  
 Služba MSMQ umožňuje používat protokol HTTP (včetně použití protokolu HTTPS) k posílání zpráv do fronty. V tomto příkladu ukážeme, že používáme komunikaci ve frontě Windows Communication Foundation (WCF) a jak odesílat zprávy přes protokol HTTP. Služba MSMQ používá protokol s názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
4. Před spuštěním ukázky v **části Přidat nebo odebrat součásti systému Windows**se ujistěte, že je služba MSMQ nainstalovaná s podporou protokolu HTTP. Instalace podpory protokolu HTTP automaticky nainstaluje Internetová informační služba (IIS) a přidá podporu protokolu ve službě IIS pro službu MSMQ.  
  
5. Pokud chcete mít jistotu, že se protokol HTTP používá ke komunikaci, můžete povolit spuštění služby MSMQ v zesíleném režimu. Tím se zajistí, že žádné zprávy, které se na tomto počítači hostují, nemůžou dorazit pomocí jakéhokoli přenosu bez protokolu HTTP.  
  
6. Po vybrání možnosti MSMQ pro spuštění v zesíleném režimu vyžaduje počítač opětovné spuštění v systému Windows Server 2003.  
  
7. Spusťte službu.  
  
8. Spusťte klienta. Ujistěte se, že jste změnili adresu koncového bodu tak, aby odkazovala na název počítače nebo IP adresu namísto localhost. Klient pošle zprávu a ukončí se.  
  
## <a name="requirements"></a>Požadavky  
 Aby bylo možné tuto ukázku spustit, musí být služba IIS nainstalována kromě služby MSMQ do služby i klientských počítačů.  
  
## <a name="demonstrates"></a>Demonstruje  
 Ukázka ukazuje, jak odesílat zprávy ve frontě WCF pomocí služby MSMQ přes HTTP. Tato služba se také nazývá zpráva SRMP. Při odeslání zprávy ve frontě přenáší MSMQ na odesílajícím počítači zprávy do přijímacího správce front přes přenos přes protokol TCP nebo HTTP. Zvolíte-li protokol SRMP, uživatel určí možnost protokolu HTTP jako přenosu pro přenos fronty. Protokol SRMP Secure umožňuje použití protokolu HTTPS.  
  
## <a name="example"></a>Příklad  
 Vzorový kód je založený na ukázce v transakčním režimu. Způsob odeslání zprávy do fronty a příjem zprávy z fronty pomocí protokolu SRMP je stejný jako odesílání a příjem zpráv pomocí nativního protokolu.  
  
 Konfigurace klienta se změnila tak, aby označovala možnost protokolu přenosu fronty. Přenosový protokol fronty může být jeden z nativních, SRMP nebo SrmpSecure. Ve výchozím nastavení je přenosový protokol nativní. Klient a služba v tomto příkladu určují v konfiguraci použití SRMP.  
  
 V souvislosti se zabezpečením přenosu existují omezení protokolu SRMP. Výchozí zabezpečení přenosu služby MSMQ vyžaduje službu Active Directory, která vyžaduje, aby se správce fronty odesílání a přijímací správce fronty nacházel ve stejné doméně systému Windows. Při posílání zpráv přes hranice HTTP to není možné. V takovém případě výchozí zabezpečení přenosu nefunguje. Pokud je požadováno zabezpečení přenosu, musí být zabezpečení přenosu nastaveno na certifikát. Zabezpečení zpráv lze také použít k zabezpečení zprávy. V této ukázce je pro ilustraci zpráv protokolu SRMP vypnutá jak přenos, tak zabezpečení zpráv.  
  
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
  
 Spuštění ukázky poskytne následující výstup.  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  

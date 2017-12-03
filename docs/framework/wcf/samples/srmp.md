---
title: SRMP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b33ecabb6796ee123e27213a92b6b0d7aefaf9a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="srmp"></a>SRMP
Tato ukázka ukazuje, jak provést zpracovaných komunikace ve frontě pomocí služby Řízení front zpráv (MSMQ) přes protokol HTTP.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 MSMQ umožňuje použití protokolu HTTP (včetně použití protokolu HTTPS) k odesílání zpráv do fronty. V tomto příkladu jsme demonstruje použití [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zařazených do fronty komunikace a odesílání zpráv přes protokol HTTP. MSMQ používá protokol názvem SRMP, což je protokol založený na protokolu SOAP pro komunikaci přes protokol HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Před spuštěním ukázky **přidat nebo odebrat součásti systému Windows**, ujistěte se, že služba MSMQ je nainstalována s podporou protokolu HTTP. Instalace podpory protokolu HTTP automaticky nainstaluje Internetové informační služby (IIS) a přidává podporu protokolu ve službě IIS pro službu MSMQ.  
  
5.  Pokud chcete mít jistotu, že protokol HTTP se používá pro komunikaci, můžete povolit služby MSMQ v zesíleném režimu. Tím se zajistí, že žádné zprávy do fronty, všechny hostované na počítači můžete doručeny použití jakékoli přenosu jiným protokolem než HTTP.  
  
6.  Po výběru služby MSMQ v zesíleném režimu, daný počítač vyžaduje znovu spustit na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Spusťte službu.  
  
8.  Spuštění klienta. Ujistěte se, že změníte adresa koncového bodu tak, aby odkazoval na název počítače nebo IP adresu místo localhost. Klient odešle zprávu a ukončí.  
  
## <a name="requirements"></a>Požadavky  
 Pokud chcete tuto ukázku spustit, služba IIS musí být nainstalován na službu a klientské počítače kromě služby MSMQ.  
  
## <a name="demonstrates"></a>Demonstruje  
 Ukázka ukazuje odesílání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zařazených do fronty zpráv přes protokol HTTP pomocí služby MSMQ. To je také označován SRMP zasílání zpráv. Když je odeslána zpráva zařazených do fronty, MSMQ na odesílání přenosů počítač zprávy, aby se využívá správce fronty pomocí přenosového protokolu TCP nebo HTTP. Výběrem SRMP označuje uživatele volba HTTP přenos pro přenos fronty. Zabezpečení SRMP umožňuje použití protokolu HTTPS.  
  
## <a name="example"></a>Příklad  
 Ukázkový kód je založena na zpracovaných vzorku. Jak odeslat zprávu do fronty a přijímat zprávy z fronty pomocí SRMP je stejný jako odesílání a přijímání zpráv pomocí nativního protokolu.  
  
 Konfigurace pro klienta se změní na znamenat výběr protokol fronty přenosu. Protokol fronty přenosu může mít jednu z nativní, SRMP nebo SrmpSecure. Ve výchozím nastavení je přenos protokolu nativní. Klient a služba zadejte v konfiguraci použít SRMP v tomto příkladu.  
  
 Je třeba SRMP omezení ve vztahu k zabezpečení přenosu. Zabezpečení přenosu služby MSMQ výchozí vyžaduje služby Active Directory, která vyžaduje, aby správce fronty odesílání a příjmu správce front jsou umístěny ve stejné doméně systému Windows. To není možné při odesílání zpráv přes HTTP hranici. Zabezpečení přenosu výchozí jako takový nefunguje. Zabezpečení přenosu musí být nastavena na certifikát, pokud se požaduje zabezpečení přenosu. Zabezpečení zpráv lze také zabezpečit zprávy. V této ukázce je zabezpečení přenosu a zprávy pro ilustraci zasílání zpráv SRMP vypnutý.  
  
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
  
 Spuštění ukázky vypočítá následující výstup.  
  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a>Viz také

---
title: Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: 7e1c5ae0cb1a44c72a27566035b4bc20acbf1614
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214014"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
Tato ukázka předvádí, jak zjistit službu, která má <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> nastavenou na <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Když <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, identifikátorem ListenUri je, že jsou splněné být jedinečný, tak, že nastavíte jedinečný port nebo pro cestu být jedinečný identifikátor GUID připojením.  
  
### <a name="features-on-the-service"></a>Funkce služby  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique> pro koncový bod TCP. Služba poté je proveden zjistitelný prostřednictvím <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncového bodu.  
  
### <a name="features-on-the-client"></a>Funkce na straně klienta  
 Tento klient připojí ke službě pomocí správné `Via.Uri` pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody. <xref:System.ServiceModel.Discovery.FindResponse> Vrácené z metody pak dotaz na tom, zda obsahuje platné <xref:System.ServiceModel.Endpoint.ListenUri%2A> a určuje, zda se liší od `Address.Uri`. Příslušné informace je pak předán `InvokeCalculatorService` metody. V `InvokeCalculatorService` metody <xref:System.ServiceModel.Endpoint.ListenUri%2A> byla předána volajícím, o `ClientViaBehavior` se správnými `Via.Uri` se přidá do koncového bodu klienta.  
  
##### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete UniqueListenUriMode.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Spusťte aplikaci služby, který je generován ve složce \service\bin\debug [základní adresář řešení].  
  
4.  Spuštění klientské aplikace, který je generován ve složce \Client\bin\debug [základní adresář řešení].  
  
     Klient vyhledá spuštěnou službu a zapisuje do konzoly metadat publikoval(a) koncového bodu služby.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Viz také

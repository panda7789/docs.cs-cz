---
title: Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: e6129594df6170f94a06caa08a9f16e4770bbfd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501452"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Ukázka zjišťování služby s vlastností ListenUriMode nastavenou na Unique
Tento příklad ukazuje, jak zjistit službu, která má <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> vlastnost nastavena na hodnotu <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Když <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, je zajištěno, že adrese ListenUri být jedinečný, a to nastavením portu být jedinečný, nebo pro danou cestu jako jedinečný identifikátor GUID připojením.  
  
### <a name="features-on-the-service"></a>Funkce ve službě  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Je nastavena na <xref:System.ServiceModel.Description.ListenUriMode.Unique> pro koncový bod TCP. Služba je potom k zjistitelný prostřednictvím <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> koncový bod.  
  
### <a name="features-on-the-client"></a>Funkce na straně klienta  
 Tento klient připojí ke službě pomocí správného `Via.Uri` pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda. <xref:System.ServiceModel.Discovery.FindResponse> , Vrátí metoda je pak dotazován na tom, zda obsahuje platné <xref:System.ServiceModel.Endpoint.ListenUri%2A> a jestli je jiný než `Address.Uri`. Příslušné informace, které se pak předá do `InvokeCalculatorService` metoda. V `InvokeCalculatorService` metoda, <xref:System.ServiceModel.Endpoint.ListenUri%2A> byla předaná volající funkcí, pak `ClientViaBehavior` s správný `Via.Uri` je přidána ke koncovému bodu klienta.  
  
##### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete UniqueListenUriMode.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Spusťte aplikaci služby, která se generují ve složce \service\bin\debug [základní adresář řešení].  
  
4.  Spusťte klientskou aplikaci, která se generují ve složce \Client\bin\debug [základní adresář řešení].  
  
     Klient vyhledá spuštěnou službu a zapíše do konzoly metadat, které zveřejnil koncový bod služby.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Viz také

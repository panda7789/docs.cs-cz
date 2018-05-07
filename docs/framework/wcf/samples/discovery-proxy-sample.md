---
title: Ukázka proxy serveru zjišťování
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: e9cbfcb717f502a849d4d508d13df6c00b95db58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="discovery-proxy-sample"></a>Ukázka proxy serveru zjišťování
Tento příklad ukazuje, jak vytvořit implementace zjišťování proxy k uložení informací o existujících služeb a jak se klienti mohou odesílat dotazy tento proxy server pro informace. Tato ukázka se skládá ze tří projektů:  
  
-   **Služba**: jednoduchý kalkulačky služba Windows Communication Foundation (WCF), která registruje zjišťování proxy.  
  
-   **Zjišťování Proxy**: Implementace zjišťování proxy služby.  
  
-   **Klient**: A WCF klientskou aplikaci, která volá zjišťování proxy k vyhledání služeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Implementace proxy zjišťování  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 V `Main` metoda souboru Program.cs příklad ukazuje, jak službu typu <xref:System.ServiceModel.Discovery.DiscoveryProxy> je hostovaná. Poskytuje dva koncové body, jeden typ <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> a další typu <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Oba koncových bodů TCP používají jako přenosového mechanismu. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Naslouchá na identifikátoru URI určeného `probeEndpointAddress` parametr, to je, kde klienti mohou zasílat zprávy testu dotazovat proxy server pro svoje data. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Naslouchá na identifikátoru URI určeného `announcementEndpointAddress` parametr. Toto je, kde proxy server naslouchá na oznámení. Po přijetí oznámení online proxy server přidá do své mezipaměti služby a po přijetí oznámení offline odebere službu ze své mezipaměti.  
  
 DiscoveryProxy.cs obsahuje implementace <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Proxy server musí dědit z <xref:System.Object> třídy a vyžaduje implementaci <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Při vytváření instancí, vytvoří novou Proxy <xref:System.Collections.Generic.Dictionary%602>, který se používá k uložení elementy ví o.  
  
 Soubor je rozdělené do dvou oblastí, metody mezipaměti Proxy a implementace Proxy zjišťování. Oblasti Proxy mezipaměti metody obsahuje metody, které používá k aktualizaci <xref:System.Collections.Generic.Dictionary%602>, provádět dotazy proti <xref:System.Collections.Generic.Dictionary%602>a tisk dat pro uživatele. Implementace Proxy zjišťování oblast obsahuje přepsané metody požadované pro funkci oznámení a kontroly. Že definují akce prováděné na serveru proxy, po přijetí Online oznámení, oznámení do režimu Offline nebo test zprávy.  
  
## <a name="service"></a>Služba  
 V souboru Program.cs v projektu služby se stejným identifikátorem URI používá pro svůj koncový bod oznámení jako proxy server zjišťování. Je to proto, že služba používá pro odesílání oznámení, zatímco proxy serveru se používá pro příjem je koncový bod. Služba používá <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> a přidá do něj koncový bod oznámení.  
  
## <a name="client"></a>Klient  
 Projektu klienta používá stejný identifikátor URI pro svůj koncový bod testu jako proxy server. To je proto sondy v tomto scénáři jsou zároveň jednosměrového vysílání určený speciálně pro koncový bod k dispozici na proxy serveru. Klient připojí k této známou adresu a potom se dotazuje služby. Po nalezení služby, ke kterému je připojen k němu.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načtení projektu řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.  
  
2.  Nejprve spuštěním zjišťování Proxy aplikace, vygenerovaných \DiscoveryProxy\bin\debug [základní adresář řešení]. Zjišťování Proxy musí nejprve spustit, protože koncové body TCP oznámení musí být pro službu pro odeslání jeho oznámení.  
  
3.  Druhý spusťte aplikaci služby vygenerovaných \Service\bin\debug [základní adresář řešení]. Při spouštění služba odesílá oznámení oznámení koncový bod zjišťování serveru proxy a je zaregistrován v mezipaměti k proxy serveru.  
  
4.  V dalším kroku spusťte klientskou aplikaci, vygenerovaných \Client\bin\debug [základní adresář řešení]. Klient dotazuje proxy server, získá adresu služby a potom připojí ke službě.  
  
5.  Ukončete nakonec klient služby a proxy server. Proxy server musí používat pro příjem oznámení služby offline.  
  
## <a name="see-also"></a>Viz také

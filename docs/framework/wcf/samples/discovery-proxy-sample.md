---
title: Ukázka proxy serveru zjišťování
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: 6fc0680bc6b61a6fe1b4b141c8b1e5081df5a124
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892370"
---
# <a name="discovery-proxy-sample"></a>Ukázka proxy serveru zjišťování
Tato ukázka předvádí, jak vytvořit implementace zjišťování proxy k ukládání informací o existujících služeb a jak můžou klienti dotazovat tohoto proxy informace. Tato ukázka se skládá ze tří projektů:  
  
-   **Služba**: jednoduché služba kalkulačky Windows Communication Foundation (WCF), která se zaregistruje ve službě proxy zjišťování.  
  
-   **Proxy zjišťování**: Implementace zjišťování proxy službu.  
  
-   **Klient**: A WCF klientská aplikace, která volá zjišťování proxy k vyhledání služeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Implementace proxy zjišťování  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>Objektu DiscoveryProxy  
 V `Main` metoda souboru Program.cs Tato ukázka vysvětluje, jak službu typu <xref:System.ServiceModel.Discovery.DiscoveryProxy> hostována. Poskytuje dva koncové body, jeden z typů <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> a druhou typu <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Oba koncové body TCP používají jako přenosového mechanismu. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Naslouchání na identifikátoru URI určeného `probeEndpointAddress` parametr, to je, kde klienti odesílat zprávy o testu k dotazování proxy pro svá data. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Naslouchání na identifikátoru URI určeného `announcementEndpointAddress` parametru. To je, ve kterém proxy server naslouchá oznámení. Po přijetí oznámení online proxy server přidá do mezipaměti služby a po přijetí oznámení offline odebere službu uloženou v mezipaměti.  
  
 DiscoveryProxy.cs obsahuje implementaci <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Proxy server musí dědit z <xref:System.Object> třídy a vyžaduje implementace <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Při vytváření instance, vytvoří nový proxy server <xref:System.Collections.Generic.Dictionary%602>, kterou používá pro ukládání prvků ví o.  
  
 Soubor je rozdělen do dvou oblastí, metody mezipaměti proxy serveru a implementace zjišťování proxy serveru. Oblast metody mezipaměti proxy serveru obsahuje metody, které používá k aktualizaci <xref:System.Collections.Generic.Dictionary%602>, provádění dotazů <xref:System.Collections.Generic.Dictionary%602>a tisknout data pro uživatele. Implementace Proxy zjišťování oblasti obsahuje přepsané metody požadované pro funkci oznámení a kontroly. Definují akce prováděné na proxy serveru po přijetí Online oznámení, oznámení v režimu Offline nebo průzkumné zprávy.  
  
## <a name="service"></a>Služba  
 V souboru Program.cs v projektu služby se stejným identifikátorem URI používá pro svůj koncový bod oznámení jako proxy zjišťování. Je to proto, že služba používá koncový bod pro zasílání oznámení, když proxy server použije pro jejich přijetí. Služba používá <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> a přidá do něj koncový bod oznámení.  
  
## <a name="client"></a>Klient  
 Klientský projekt používá stejný identifikátor URI pro svůj koncový bod jako proxy server. Je to proto, že testy v tomto scénáři se také jednosměrového vysílání speciálně pro koncový bod k dispozici na proxy serveru. Klient připojí k této adrese dobře známé a dotazuje se na službu. Po nalezení službu, kterou se připojí k němu.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načítání řešení projektu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a sestavte projekt.  
  
2.  Nejprve spusťte aplikaci Proxy zjišťování, vygenerované v \DiscoveryProxy\bin\debug [základní adresář řešení]. Zjišťování Proxy musí nejdřív spustit, protože koncové body TCP oznámení musí být pro službu pro odeslání jeho oznámení.  
  
3.  Za druhé spuštění služby aplikace vygenerované v \Service\bin\debug [základní adresář řešení]. Při spouštění služba odesílá oznámení do koncového bodu oznámení proxy zjišťování a je zaregistrovaný v mezipaměti proxy serveru.  
  
4.  V dalším kroku spuštění klientské aplikace vygenerované v \Client\bin\debug [základní adresář řešení]. Klient dotazuje serveru proxy, získá adresu služby a poté se připojí ke službě.  
  
5.  Ukončete nakonec klient služby a proxy serveru. Proxy server musí být spuštěná, aby se dostávat oznámení služby v režimu offline.  
  
## <a name="see-also"></a>Viz také

---
title: "Hledání zjišťování a kritéria hledání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b367b5133cd765fe7e160cd2706589c1773eeb59
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-find-and-findcriteria"></a>Hledání zjišťování a kritéria hledání
Operaci hledání zjišťování se spouští pomocí klienta ke zjištění jednu nebo více služeb a je jedním z hlavní akce v zjišťování. Provádění najít odešle zprávu WS-Discovery Probe přes síť. Služby, které odpovídají kritériím zadaným WS-Discovery ProbeMatch zprávy odpovědi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zjišťování zprávy, najdete v článku [specifikaci WS-Discovery](http://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>Objekty DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Třída poskytuje mechanismus k provádění operací hledání a díky provádění operací klienta zjišťování snadné. Obsahuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která provede (blokování) synchronní najít, a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metodu, která zahájí asynchronní hledání neblokující. Obě metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> parametr a zajistit výsledky pro uživatele prostřednictvím <xref:System.ServiceModel.Discovery.FindResponse> objektu.  
  
## <a name="findcriteria"></a>Kritéria hledání  
 <xref:System.ServiceModel.Discovery.FindCriteria>má několik vlastností, které je možné seskupit do kritéria hledání, které určují, jaké služby, které hledáte, a najít ukončení kritéria (jak dlouho by měl poslední hledání). A <xref:System.ServiceModel.Discovery.FindCriteria> může obsahovat více kritérií vyhledávání. Ve výchozím nastavení, musí odpovídat všechny součásti služby jinak nebere v úvahu samotné odpovídající služby. Pokud chcete najít služby, které odpovídá pouze některá kritéria, můžete implementovat vlastní najít logiku na službu nebo můžete použít více dotazů.  
  
 Kritéria vyhledávání patří:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>-Volitelné. Název kontraktu služby vyhledána a kritéria obvykle používaných při hledání služby. Pokud je zadán více než jeden název kontraktu, odpovědět pouze koncové body služby odpovídající všechny smlouvy. Všimněte si, že v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod podporuje pouze jeden kontrakt.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>-Volitelné. Obory jsou absolutní identifikátory URI, který slouží ke kategorizaci koncových bodů jednotlivých služeb. Můžete použít ve scénářích, kde několik koncových bodů vystavit stejné smlouvy a chcete způsob, jak hledat pro podmnožinu koncových bodů. Pokud je zadán více než jednoho oboru, odpovědět pouze koncové body služby odpovídající všechny obory.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-Určuje odpovídající algoritmus použitý při odpovídající obory ve zprávě test s u koncového bodu. Existují pravidla pět odpovídající oboru podporované:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>porovnání řetězců základní malá a velká písmena.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>odpovídá segmenty oddělených "/". Vyhledejte http://contoso/building1 odpovídá služby s http://contoso/building/floor1 oboru. Všimněte si, že neodpovídá http://contoso/building100 vzhledem k tomu, že poslední dva segmenty se neshodují.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>odpovídá obory segmentů pomocí adresy URL protokolu LDAP.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>odpovídá obory přesně pomocí řetězce UUID.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>odpovídá pouze služby, které neurčují obor.  
  
     Pokud není zadán obor odpovídající pravidlo, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> se používá.  
  
 Ukončení kritéria patří:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>-Maximální doba čekání na odpovědi od služby v síti. Výchozí doba je 20 sekund.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>-Maximální počet odpovědí čekání. Pokud <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpovědi jsou obdrženy předtím, než <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynul skončení operace hledání.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse>má <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> vlastnost kolekce, která obsahuje všechny odpovědi poslal odpovídající služby v síti. Pokud žádné služby zodpovězených, kolekce je prázdná. Pokud jeden nebo více služeb zodpovězených, každou odpověď je uložen v <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> objektu, který obsahuje adresu, kontrakt a některé další informace o službě.  
  
 Následující příklad ukazuje, jak provádět operace hledání v kódu.  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Pomocí kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Asynchronní hledání](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Základní](../../../../docs/framework/wcf/samples/basic-sample.md)

---
title: Hledání zjišťování a kritéria hledání
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 6efbfe34bbe5b15696d247c291f1d88006a53a36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345778"
---
# <a name="discovery-find-and-findcriteria"></a>Hledání zjišťování a kritéria hledání
Operace hledání zjišťování inicializuje klienta ke zjištění jednu nebo více služeb a je jedním z hlavní akce zjišťování. Provádění najít odešle zprávu WS-Discovery Probe přes síť. Služby, které odpovídají kritériím zadaným zprávy WS-Discovery ProbeMatch odpověď. Další informace o zjišťování zpráv, najdete v článku [specifikace WS-Discovery](https://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Třída poskytuje mechanismus k provedení operace hledání a usnadňuje provádění zjišťování klientské operace snadné. Obsahuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která provádí synchronní hledání (blokování), a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metodu, která zahájí asynchronní hledání bez blokování. Obě metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> parametr a k poskytování výsledků pro uživatele provede <xref:System.ServiceModel.Discovery.FindResponse> objektu.  
  
## <a name="findcriteria"></a>Kritéria hledání  
 <xref:System.ServiceModel.Discovery.FindCriteria> má několik vlastností, které mohou být seskupeny do kritéria hledání, které určují, jaké služby, které hledáte, a najít ukončení kritéria (jak dlouho vyhledávání by měl trvat). A <xref:System.ServiceModel.Discovery.FindCriteria> může obsahovat více kritériím hledání. Ve výchozím nastavení, musí odpovídat všechny komponenty služby jinak se neberou v úvahu samotné odpovídající služby. Pokud chcete najít služby, které odpovídá pouze některá kritéria, můžete implementovat vlastní najít logiku na službu nebo můžete použít více dotazů.  
  
 Zahrnují kritéria vyhledávání:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> – Volitelné. Název kontraktu služby vyhledaly a kritéria obvykle používá při vyhledávání pro službu. Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovědět. Všimněte si, že ve službě WCF koncový bod podporuje pouze jeden kontrakt.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> – Volitelné. Obory jsou absolutní URI, které slouží ke kategorizaci koncových bodů jednotlivých služeb. Můžete využít v situacích, kdy několik koncových bodů vystavit stejný kontrakt a chcete, aby způsob, jak hledat pro celou dílčí sadu koncových bodů. Pokud je zadán více než jednoho oboru, odpovědět jenom koncové body služby odpovídající všechny obory.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -Určuje porovnávací algoritmus, který bude použit při porovnání rozsahů průzkumné zprávy, která koncového bodu. Existují pravidla pět oboru odpovídajícím podporované:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> porovnání řetězců základní malá a velká písmena.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> shody podle segmentů oddělených pomocí "/". Hledání `http://contoso/building1` odpovídá služby s oborem `http://contoso/building/floor1`. Všimněte si, že neodpovídá `http://contoso/building100` vzhledem k tomu, že poslední dva segmenty se neshodují.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> Porovná obory podle segmentů pomocí adresy URL protokolu LDAP.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> odpovídá přesně pomocí řetězce UUID obory.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> odpovídá pouze ty služby, které není zadán obor.  
  
     Pokud není zadán obor odpovídající pravidlo, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> se používá.  
  
 Ukončení kritéria patří:  
  
1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> – Maximální dobu čekání na odpovědi služby v síti. Výchozí doba je 20 sekund.  
  
2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> – Maximální počet odpovědí čekání. Pokud <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpovědi jsou obdrženy předtím, než <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynutí skončí operace find.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> má <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> vlastnost kolekce, která obsahuje veškeré odpovědi odeslané to provede spárováním odpovídajících služby v síti. Pokud příjemce odpovědi žádné služby, kolekce je prázdná. Pokud jeden nebo více služeb odpověděl, každá odpověď je uložené v <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> objektu, který obsahuje adresu, kontrakt a některé další informace o službě.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Použití kanálu klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
- [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Základy](../../../../docs/framework/wcf/samples/basic-sample.md)

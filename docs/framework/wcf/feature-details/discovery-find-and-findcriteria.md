---
title: Hledání zjišťování a kritéria hledání
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: da4c3c4a1d765e4f91b03f4f8fc1a73c3fea1535
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964834"
---
# <a name="discovery-find-and-findcriteria"></a>Hledání zjišťování a kritéria hledání

Operace hledání zjišťování je iniciována klientem, aby zjistila jednu nebo více služeb a je jednou z hlavních akcí zjišťování. Při provádění funkce Find se přes síť pošle zpráva sondy WS-Discovery. Služby, které odpovídají zadaným kritériím s odpovědí WS-Discovery ProbeMatch Messages. Další informace o zprávách zjišťování najdete v tématu [specifikace WS-Discovery](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>Objektem DiscoveryClient zahozena

Třída <xref:System.ServiceModel.Discovery.DiscoveryClient> poskytuje mechanismus pro provádění operací hledání a usnadňuje provádění operací klienta zjišťování. Obsahuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která provádí (blokující) synchronní hledání a metodu <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>, která iniciuje neblokované asynchronní hledání. Obě metody přijímají parametr <xref:System.ServiceModel.Discovery.FindCriteria> a poskytují uživatelům výsledky prostřednictvím objektu <xref:System.ServiceModel.Discovery.FindResponse>.

## <a name="findcriteria"></a>Kritéria hledání

<xref:System.ServiceModel.Discovery.FindCriteria> má několik vlastností, které mohou být seskupeny do vyhledávacích kritérií, které určují, jaké služby hledáte, a najít kritéria ukončení (jak dlouho má hledání trvat). <xref:System.ServiceModel.Discovery.FindCriteria> může obsahovat více kritérií hledání. Ve výchozím nastavení musí služba odpovídat všem součástem, jinak se nepovažuje za odpovídající službu. Pokud chcete najít služby, které odpovídají pouze některým kritériím, můžete implementovat vlastní logiku hledání na službu nebo můžete použít více dotazů.

Kritéria hledání zahrnují:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> – volitelné. Název kontraktu prohledávané služby a kritéria, která se obvykle používají při hledání služby. Je-li zadán více než jeden název kontraktu, odpovídá pouze koncové body služby odpovídající všem smlouvám. Všimněte si, že v WCF může koncový bod podporovat jenom jednu kontrakt.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> – volitelné. Obory jsou absolutní identifikátory URI, které slouží k kategorizaci jednotlivých koncových bodů služby. Můžete ho chtít použít ve scénářích, kdy více koncových bodů zveřejňuje stejný kontrakt a chcete vyhledat podmnožinu koncových bodů. Je-li zadán více než jeden obor, odpovídá pouze koncovým bodům služby, které odpovídají všem oborům.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> – určuje odpovídající algoritmus, který se použije při porovnání oborů v rámci zprávy sondy s bodem koncového bodu. Existuje pět podporovaných pravidel pro porovnání oboru:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> používá standardní porovnávání řetězců s rozlišováním velkých a malých písmen.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> odpovídá segmentům odděleným znakem "/". Hledání `http://contoso/building1` odpovídá službě s rozsahem `http://contoso/building/floor1`. Všimněte si, že neodpovídá `http://contoso/building100`, protože poslední dva segmenty se neshodují.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> odpovídá oborům podle segmentů pomocí adresy URL protokolu LDAP.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> přesně odpovídá rozsahům pomocí řetězce UUID.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> odpovídá pouze službám, které neurčují obor.

  Pokud není zadáno pravidlo pro porovnání s oborem, je <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> použito.

Mezi kritéria ukončení patří:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> – maximální doba čekání na odpovědi ze služeb v síti. Výchozí doba trvání je 20 sekund.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> – maximální počet odpovědí, na které se má čekat. Pokud <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> odpovědi byly přijaty před <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynula, operace hledání skončí.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse> má vlastnost kolekce <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A>, která obsahuje všechny odpovědi odeslané odpovídajícími službami v síti. Pokud žádné služby neodpoví, je kolekce prázdná. Pokud jedna nebo více služeb odpovědělo, každá odpověď se uloží do objektu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, který obsahuje adresu, kontrakt a další informace o této službě.

Následující příklad ukazuje, jak provést operaci Find v kódu.

```csharp
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

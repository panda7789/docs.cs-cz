---
title: Hledání zjišťování a kritéria hledání
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 1d6a0e3fcca45c3fe57aab84b0f2b6b86fabb404
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599175"
---
# <a name="discovery-find-and-findcriteria"></a>Hledání zjišťování a kritéria hledání

Operace hledání zjišťování je iniciována klientem, aby zjistila jednu nebo více služeb a je jednou z hlavních akcí zjišťování. Při provádění funkce Find se přes síť pošle zpráva sondy WS-Discovery. Služby, které odpovídají zadaným kritériím s odpovědí WS-Discovery ProbeMatch Messages. Další informace o zprávách zjišťování najdete v tématu [specifikace WS-Discovery](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>Objektem DiscoveryClient zahozena

<xref:System.ServiceModel.Discovery.DiscoveryClient>Třída poskytuje mechanismus pro provádění operací hledání a usnadňuje provádění operací klienta zjišťování. Obsahuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která provádí (blokující) synchronní hledání a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metodu, která inicializuje asynchronní hledání bez blokování. Obě metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> parametr a poskytují výsledky uživateli prostřednictvím <xref:System.ServiceModel.Discovery.FindResponse> objektu.

## <a name="findcriteria"></a>Kritéria hledání

<xref:System.ServiceModel.Discovery.FindCriteria>má několik vlastností, které se dají seskupit do vyhledávacích kritérií, která určují, jaké služby hledáte a kde najdete kritéria ukončení (jak dlouho má hledání trvat). <xref:System.ServiceModel.Discovery.FindCriteria>Může obsahovat více kritérií hledání. Ve výchozím nastavení musí služba odpovídat všem součástem, jinak se nepovažuje za odpovídající službu. Pokud chcete najít služby, které odpovídají pouze některým kritériím, můžete implementovat vlastní logiku hledání na službu nebo můžete použít více dotazů.

Kritéria hledání zahrnují:

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>Volitelné. Název kontraktu prohledávané služby a kritéria, která se obvykle používají při hledání služby. Je-li zadán více než jeden název kontraktu, odpovídá pouze koncové body služby odpovídající všem smlouvám. Všimněte si, že v WCF může koncový bod podporovat jenom jednu kontrakt.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>Volitelné. Obory jsou absolutní identifikátory URI, které slouží k kategorizaci jednotlivých koncových bodů služby. Můžete ho chtít použít ve scénářích, kdy více koncových bodů zveřejňuje stejný kontrakt a chcete vyhledat podmnožinu koncových bodů. Je-li zadán více než jeden obor, odpovídá pouze koncovým bodům služby, které odpovídají všem oborům.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-Určuje odpovídající algoritmus, který se má použít, při porovnání oborů v rámci zprávy sondy s bodem koncového bodu. Existuje pět podporovaných pravidel pro porovnání oboru:

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>rozlišuje základní porovnávání řetězců.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>odpovídá segmentům odděleným znakem "/". Hledání `http://contoso/building1` odpovídá službě s oborem `http://contoso/building/floor1` . Všimněte si, že se neshoduje, `http://contoso/building100` protože poslední dva segmenty se neshodují.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>vyhledá obory podle segmentů pomocí adresy URL protokolu LDAP.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>Porovná rozsahy přesně pomocí řetězce UUID.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>odpovídá pouze službám, které neurčují obor.

  Pokud není zadáno pravidlo pro porovnání oboru, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> je použito.

Mezi kritéria ukončení patří:

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>– Maximální doba čekání na odpovědi ze služeb v síti. Výchozí doba trvání je 20 sekund.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>– Maximální počet odpovědí, na které se má čekat. Pokud <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> jsou odpovědi přijaty před <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynutím této doby, operace hledání skončí.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse>má <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> vlastnost kolekce, která obsahuje všechny odpovědi odesílané odpovídajícími službami v síti. Pokud žádné služby neodpoví, je kolekce prázdná. Pokud jedna nebo více služeb odpovědělo, každá odpověď se uloží do <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> objektu, který obsahuje adresu, kontrakt a některé další informace o této službě.

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

## <a name="see-also"></a>Viz také

- [Přehled zjišťování WCF](wcf-discovery-overview.md)
- [Použití kanálu klienta zjišťování](using-the-discovery-client-channel.md)
- [Zjišťování pomocí oborů](../samples/discovery-with-scopes-sample.md)
- [Basic](../samples/basic-sample.md)

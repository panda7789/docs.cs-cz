---
title: Zásady mezipaměti
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: 2d3d85ebd80f417ebd0fa0e619097e15f2a6a39b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048774"
---
# <a name="cache-policy"></a>Zásady mezipaměti
Zásady mezipaměti definují pravidla, která se používají k určení, jestli je možné požadavek vyhovět pomocí kopie požadovaného prostředku v mezipaměti. Aplikace určují požadavky na mezipaměť klienta na aktuálnost, ale zásady efektivních zásad mezipaměti jsou určeny požadavky na mezipaměť klienta, požadavky na vypršení platnosti obsahu serveru a požadavky na revalidy serveru. Interakce zásad mezipaměti klienta a požadavků na server vždy vede k nejzávažnějším zásadám mezipaměti, které vám pomůžou zajistit, že se k nejnovějšímu obsahu vrátí klientská aplikace.  
  
 Zásady mezipaměti jsou buď založené na umístění, nebo na základě času. Zásady mezipaměti na základě umístění definují aktuálnost záznamů uložených v mezipaměti podle toho, kde se dá požadovaný prostředek považovat. Zásady mezipaměti založené na čase definují aktuálnost záznamů uložených v mezipaměti pomocí času načtení prostředku, záhlaví vrácených s prostředkem a aktuální čas. Většina aplikací může používat výchozí zásady mezipaměti založené na čase, které implementují zásady ukládání do mezipaměti uvedené v dokumentu RFC 2616, které jsou k dispozici na webu [IETF (Internet Engineering Task Force)](https://www.ietf.org/) .  
  
 Třídy popsané v následující tabulce se používají k určení zásad mezipaměti.  
  
|Název třídy|Popis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Představuje zásady mezipaměti založené na umístění a časovou mezipaměť pro prostředky vyžádané <xref:System.Net.HttpWebRequest> pomocí objektů.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Představuje zásady mezipaměti založené na umístěních nebo <xref:System.Net.Cache.RequestCacheLevel.Default> zásady mezipaměti založené na čase pro prostředky vyžádané <xref:System.Net.WebRequest> pomocí objektů.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Určuje hodnoty, které slouží k vytváření objektů <xref:System.Net.Cache.HttpRequestCachePolicy> založených na čase.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Určuje hodnoty používané k vytvoření <xref:System.Net.Cache.HttpRequestCachePolicy> objektů založených na poloze a času.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Určuje hodnoty používané k vytvoření <xref:System.Net.Cache.RequestCacheLevel.Default> <xref:System.Net.Cache.RequestCachePolicy> objektů založených na poloze nebo časových objektů.|  
  
 Můžete definovat zásady mezipaměti pro všechny požadavky vytvořené aplikací nebo pro jednotlivé požadavky. Když zadáte obě zásady mezipaměti na úrovni aplikace i zásady mezipaměti na úrovni požadavků, použijí se zásady na úrovni požadavků. Zásady mezipaměti na úrovni aplikace můžete zadat programově nebo pomocí konfiguračních souborů aplikace nebo počítače. Další informace naleznete v tématu [ \<RequestCaching > element (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Chcete-li vytvořit zásadu mezipaměti, je nutné vytvořit objekt zásad vytvořením instance <xref:System.Net.Cache.RequestCachePolicy> třídy nebo. <xref:System.Net.Cache.HttpRequestCachePolicy> Chcete-li zadat zásadu na žádost, nastavte <xref:System.Net.WebRequest.CachePolicy%2A> vlastnost požadavku na objekt zásad. Při nastavování zásad na úrovni aplikace pomocí kódu programu <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> nastavte vlastnost na objekt zásad.  
  
 Příklady kódu, které ukazují vytváření a používání zásad mezipaměti, najdete v tématu [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)

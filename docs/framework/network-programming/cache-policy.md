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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048774"
---
# <a name="cache-policy"></a>Zásady mezipaměti
Zásada mezipaměti definuje pravidla, která se používají k určení, zda lze požadavek splnit pomocí kopie požadovaného prostředku uložené v mezipaměti. Aplikace určují požadavky mezipaměti klienta na čerstvost, ale efektivní zásady mezipaměti jsou určeny požadavky mezipaměti klienta, požadavky na vypršení platnosti obsahu serveru a požadavky na opětovné ověření serveru. Interakce zásad mezipaměti klienta a požadavků serveru vždy vede k nejkonzervativnější zásadě mezipaměti, která pomáhá zajistit, aby byl do klientské aplikace vrácen nejčerstvější obsah.  
  
 Zásady mezipaměti jsou založené na umístění nebo na čase. Zásada mezipaměti založená na umístění definuje čerstvost položek uložených v mezipaměti na základě toho, odkud lze požadovaný prostředek odebrat. Zásada mezipaměti založená na čase definuje aktuálnost položek uložených v mezipaměti pomocí času, kdy byl prostředek načten, záhlaví vrácena s prostředkem a aktuální čas. Většina aplikací může používat výchozí zásady mezipaměti založené na čase, které implementují zásady ukládání do mezipaměti zadané v souboru RFC 2616, které jsou k dispozici na webu [IETF (Internet Engineering Task Force).](https://www.ietf.org/)  
  
 Třídy popsané v následující tabulce se používají k určení zásad mezipaměti.  
  
|Název třídy|Popis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Představuje zásady mezipaměti založené na umístění <xref:System.Net.HttpWebRequest> a čase pro prostředky požadované pomocí objektů.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Představuje zásady mezipaměti <xref:System.Net.Cache.RequestCacheLevel.Default> založené na umístění nebo zásady mezipaměti založené na čase pro prostředky požadované pomocí <xref:System.Net.WebRequest> objektů.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Určuje hodnoty použité k vytvoření <xref:System.Net.Cache.HttpRequestCachePolicy> objektů založených na čase.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Určuje hodnoty použité k vytvoření <xref:System.Net.Cache.HttpRequestCachePolicy> objektů založených na umístění a času.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Určuje hodnoty použité k vytvoření objektů <xref:System.Net.Cache.RequestCacheLevel.Default> založených <xref:System.Net.Cache.RequestCachePolicy> na umístění nebo na základě času.|  
  
 Můžete definovat zásady mezipaměti pro všechny požadavky provedené vaší aplikací nebo pro jednotlivé požadavky. Pokud zadáte zásady mezipaměti na úrovni aplikace i zásady mezipaměti na úrovni požadavků, použije se zásada na úrovni požadavku. Zásady mezipaměti na úrovni aplikace můžete zadat programově nebo pomocí konfiguračních souborů aplikace nebo počítače. Další informace naleznete v [ \<tématu requestCaching> Element (Network Settings).](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)  
  
 Chcete-li vytvořit zásadu mezipaměti, musíte vytvořit objekt <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> zásad vytvořením instance třídy nebo. Chcete-li určit zásadu v požadavku, <xref:System.Net.WebRequest.CachePolicy%2A> nastavte vlastnost požadavku na objekt zásady. Při programovém nastavení zásady na <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> úrovni aplikace nastavte vlastnost na objekt zásady.  
  
 Příklady kódu, které ukazují vytváření a používání zásad mezipaměti, naleznete [v tématu Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)

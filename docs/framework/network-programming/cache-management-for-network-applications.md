---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048878"
---
# <a name="cache-management-for-network-applications"></a>Správa mezipaměti pro síťové aplikace
Toto téma a související dílčí témata popisují ukládání <xref:System.Net.WebClient> <xref:System.Net.WebRequest>prostředků <xref:System.Net.HttpWebRequest>získaných pomocí tříd , , a <xref:System.Net.FtpWebRequest> tříd.  
  
 Mezipaměť poskytuje dočasné úložiště prostředků, které byly požadovány aplikací. Pokud aplikace požaduje stejný prostředek více než jednou, prostředek může být vrácena z mezipaměti, aby se zabránilo režii opětovného vyžádání ze serveru. Ukládání do mezipaměti může zlepšit výkon aplikace zkrácením času potřebného k získání požadovaného prostředku. Ukládání do mezipaměti může také snížit provoz v síti snížením počtu cest na server. Při ukládání do mezipaměti zlepšuje výkon, zvyšuje riziko, že prostředek vrácený do aplikace je zastaralý, což znamená, že není totožný s prostředek, který by byly odeslány serverem, pokud ukládání do mezipaměti nebyly používány.  
  
 Ukládání do mezipaměti může umožnit neoprávněným uživatelům nebo procesům číst citlivá data. Ověřená odpověď, která je uložena v mezipaměti, může být načtena z mezipaměti bez další autorizace. Pokud je ukládání do mezipaměti <xref:System.Net.Cache.RequestCacheLevel.BypassCache> <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> povoleno, změňte na <xref:System.Net.WebRequest.CachePolicy%2A> nebo zakázat ukládání do mezipaměti pro tento požadavek.  
  
 Z důvodu obav o zabezpečení ukládání do mezipaměti se **nedoporučuje** pro scénáře střední vrstvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zásady mezipaměti](cache-policy.md)  
 Vysvětluje, co je zásada mezipaměti a jak ji definovat.  
  
 [Zásady mezipaměti na základě místa](location-based-cache-policies.md)  
 Definuje každý typ zásad mezipaměti založených na umístění, které jsou k dispozici pro prostředky protokolu HTTP a https .)  
  
 [Zásady mezipaměti na základě času](time-based-cache-policies.md)  
 Popisuje kritéria, která lze použít k přizpůsobení zásad mezipaměti založené na čase.  
  
 [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)  
 Popisuje, jak programově vytvořit zásady mezipaměti a požadavky, které používají ukládání do mezipaměti.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Net.Cache>  
 Definuje typy a výčty používané k definování zásad mezipaměti <xref:System.Net.HttpWebRequest>pro <xref:System.Net.FtpWebRequest> prostředky získané pomocí <xref:System.Net.WebRequest>, a tříd.

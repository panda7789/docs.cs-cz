---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048878"
---
# <a name="cache-management-for-network-applications"></a>Správa mezipaměti pro síťové aplikace
Toto téma a související dílčí témata popisují ukládání do mezipaměti pro <xref:System.Net.WebClient>prostředky získané pomocí tříd, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>a. <xref:System.Net.FtpWebRequest>  
  
 Mezipaměť poskytuje dočasné úložiště prostředků, které požadovala aplikace. Pokud aplikace požádá o stejný prostředek více než jednou, může být prostředek vrácen z mezipaměti, takže nebude mít na serveru nárok na jejich opětovné vyžádání. Ukládání do mezipaměti může zlepšit výkon aplikace tím, že zkracuje dobu potřebnou k získání požadovaného prostředku. Ukládání do mezipaměti může také snížit zatížení sítě tím, že se sníží počet cest k serveru. I když ukládání do mezipaměti zvyšuje výkon, zvyšuje riziko, že prostředek vrácený do aplikace je zastaralý, což znamená, že se neshoduje s prostředkem, který by byl odeslán serverem, pokud se ukládání do mezipaměti nepoužívalo.  
  
 Ukládání do mezipaměti může umožňovat neoprávněným uživatelům nebo procesům číst citlivá data. Ověřená odpověď, která je uložena v mezipaměti, může být načtena z mezipaměti bez další autorizace. Pokud je povoleno ukládání do mezipaměti, <xref:System.Net.WebRequest.CachePolicy%2A> přejděte <xref:System.Net.Cache.RequestCacheLevel.BypassCache> na <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> nebo a zakažte ukládání do mezipaměti pro tento požadavek.  
  
 Kvůli problémům se zabezpečením není ukládání do **mezipaměti doporučováno** pro scénáře střední vrstvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zásady mezipaměti](cache-policy.md)  
 Vysvětluje, co je zásada mezipaměti a jak ji definovat.  
  
 [Zásady mezipaměti na základě místa](location-based-cache-policies.md)  
 Definuje každý typ zásad mezipaměti na základě umístění dostupných pro prostředky http a HTTPS (Hypertext Transfer Protocol).  
  
 [Zásady mezipaměti na základě času](time-based-cache-policies.md)  
 V této části najdete popis kritérií, která lze použít k přizpůsobení zásad mezipaměti založeného na čase.  
  
 [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)  
 Popisuje způsob, jak programově vytvářet zásady mezipaměti a požadavky, které používají ukládání do mezipaměti.  
  
## <a name="reference"></a>Reference  
 <xref:System.Net.Cache>  
 Definuje typy a výčty používané k definování zásad mezipaměti pro prostředky získané pomocí <xref:System.Net.WebRequest>tříd, <xref:System.Net.HttpWebRequest>a <xref:System.Net.FtpWebRequest> .

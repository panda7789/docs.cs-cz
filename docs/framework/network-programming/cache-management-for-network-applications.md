---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 265b4e451ebb76dbabe0d3e0df065504a3891f32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033160"
---
# <a name="cache-management-for-network-applications"></a>Správa mezipaměti pro síťové aplikace
Toto téma a další související části popisují, ukládání do mezipaměti pro prostředky získané s použitím <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.  
  
 Mezipaměť poskytuje dočasného úložiště prostředků, které bylo vyžádáno aplikací. Pokud aplikace požaduje více než jednou. stejný prostředek, prostředek mohou být vráceny z mezipaměti, není zpomalován režií na znovu vyžádat ze serveru. Ukládání do mezipaměti může zlepšit výkon aplikace tím, že snižuje čas potřebný k získání požadovaný prostředek. Ukládání do mezipaměti může také snížit síťový provoz snížením počtu zpráv se serverem. Při ukládání do mezipaměti zvyšuje výkon, jeho hodnota se zvyšuje riziko, že prostředek vrátil do aplikace je zastaralé, což znamená, že není stejný jako prostředek, který by se odeslaly server v případě ukládání do mezipaměti nebyly používá.  
  
 Neoprávnění uživatelé nebo procesy čtení citlivých dat můžou povolit ukládání do mezipaměti. Ověřená odpověď, která se uloží do mezipaměti může načíst z mezipaměti bez další oprávnění. Pokud je povoleno ukládání do mezipaměti, změňte na <xref:System.Net.WebRequest.CachePolicy%2A> k <xref:System.Net.Cache.RequestCacheLevel.BypassCache> nebo <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> zakázat ukládání do mezipaměti pro tento požadavek.  
  
 Ukládání do mezipaměti je z bezpečnostních důvodů **není** doporučuje pro scénáře střední vrstvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 Vysvětluje, jaké zásady mezipaměti je a jak definovat jeden.  
  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Definuje jednotlivé typy zásad mezipaměti na základě umístění k dispozici pro protokol HTTP (http a https) zdroje.  
  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Popisuje kritéria, která slouží k přizpůsobení zásad mezipaměti na základě času.  
  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Popisuje, jak prostřednictvím kódu programu vytvořit zásady mezipaměti a požadavky, které využívají ukládání do mezipaměti.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Net.Cache>  
 Definuje typy a výčty, které slouží k definování zásad mezipaměti pro prostředky získané s použitím <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.

---
title: "Správa mezipaměti pro síťové aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b960942d17e402b333354bbd932cf63d11b1209f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cache-management-for-network-applications"></a>Správa mezipaměti pro síťové aplikace
Toto téma a jeho souvisejících dílčí témata popisují ukládání do mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.  
  
 Mezipaměť poskytuje dočasné úložiště prostředků, která vyžadovala aplikace. Pokud aplikace vyžaduje stejného zdroje více než jednou, mohou být vráceny prostředek z mezipaměti, není zpomalován režií znovu požadovat ze serveru. Ukládání do mezipaměti můžete zlepšit výkon aplikací snížením čas potřebný k získání požadovaný prostředek. Ukládání do mezipaměti může také snížit zatížení sítě snížením počtu cest k serveru. Při ukládání do mezipaměti zvyšuje výkon, jeho hodnota se zvyšuje riziko, že prostředek vrátí do aplikace je zastaralé, což znamená, že není stejný jako prostředek, který by byly odeslány server v případě ukládání do mezipaměti nebyly používán.  
  
 Ukládání do mezipaměti může povolit neoprávněnými uživateli a procesy, které slouží ke čtení citlivá data. Ověřená odpověď, který je uložený v mezipaměti může načíst z mezipaměti bez další autorizace. Pokud je povoleno ukládání do mezipaměti, změňte <xref:System.Net.WebRequest.CachePolicy%2A> k <xref:System.Net.Cache.RequestCacheLevel.BypassCache> nebo <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> zakázání ukládání do mezipaměti pro tuto žádost.  
  
 Ukládání do mezipaměti je z důvodu zabezpečení se **není** doporučeno pro scénáře střední vrstvy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 Vysvětluje, jaké zásady mezipaměti je a jak definovat jeden.  
  
 [Na základě umístění mezipaměti zásad](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Definuje každý typ zásady na základě umístění mezipaměti, které jsou k dispozici pro protokol HTTP (http a https) prostředky.  
  
 [Zásady založené na čase mezipaměti](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Popisuje kritéria, která slouží k přizpůsobení zásady mezipaměti založené na čase.  
  
 [Konfigurace ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Popisuje postup vytváření zásad mezipaměti a požadavky, které používají ukládání do mezipaměti prostřednictvím kódu programu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Net.Cache>  
 Definuje typy a výčty používaný k definování zásady mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.

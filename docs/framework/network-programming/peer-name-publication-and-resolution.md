---
title: "Název publikace peer a řešení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 581d06930240022ae8792c02674d26491f44fa06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="peer-name-publication-and-resolution"></a>Název publikace peer a řešení
## <a name="publishing-a-peer-name"></a>Publikování název partnerského zařízení  
 Pokud chcete publikovat nové ID PNRP, sdílené provede následující akce:  
  
-   Odešle zprávy publikace PNRP pro své okolí mezipaměti (partnerské uzly, které registrovali PNRP ID na nejnižší úrovni mezipaměti) počáteční hodnoty své mezipaměti.  
  
-   Vybere náhodných uzly v cloudu, které nejsou své okolí a odešle je PNRP požadavky na rozlišení názvů pro vlastní ID P2P. Výsledný procesu určení koncový bod doplňuje mezipamětí náhodných uzly v cloudu s ID PNRP publikování partnerského uzlu.  
  
-  
  
 Uzly verze 2 PNRP nepublikujte PNRP ID, pokud pouze řešíme jiné ID P2P. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly = 1 hodnotu registru (typ REG_DWORD) určuje, že partnerské uzly PNRP pouze používat pro překlad názvů, nikdy pro název publikace. Tato hodnota registru můžete nakonfigurovat taky přes zásady skupiny.  
  
## <a name="resolving-a-peer-name"></a>Řešení název partnerského zařízení  
 Vyhledávání dalších partnerských uzlů v PNRP sítě nebo cloud je proces, který sestává z dvě fáze:  
  
1.  Koncový bod rozhodnutí  
  
2.  ID řešení PNRP  
  
 Ve fázi stanovení koncový bod určuje partnerského uzlu, který se pokouší vyřešit PNRP ID služby v jiném počítači, adresa IPv6 že vzdálené sdílené.  Vzdálený partner je ten, který publikována nebo je přidružený k PNRP ID počítače nebo služby.  
  
 Po potvrzení, že vzdálený koncový bod je zaregistrován do cloudu PNRP, žádajícího sdílené ve fázi řešení PNRP ID odešle žádost do tohoto koncového bodu sdílené pro ID PNRP požadované služby. Koncový bod odešle odpověď potvrzení PNRP ID služby, komentář, a až 4 kB Další informace vyžádání peer, můžete použít pro budoucí komunikaci. Například pokud požadovaný koncový bod je serverem herní, data další sdílené název záznamu může obsahovat informace o hry, úroveň play a aktuální počet přehrávače.  
  
 Ve fázi stanovení koncový bod PNRP používá iterativní proces pro lokalizaci uzlu, který publikovaná PNRP ID, ve kterém je odpovědný za kontaktování uzlů, které jsou postupně blíže k cíli PNRP ID uzlu vyřešení  
  
 Rozlišení názvů PNRP provedete partnerem prozkoumá položek v jeho vlastní mezipaměti pro položku, která odpovídá cílové ID PNRP. Pokud najde, partnerem odešle zprávu požadavku PNRP partnerovi a čeká na odpověď. Pokud záznam pro PNRP ID není nalezen, partnerem odešle zprávu požadavku PNRP na partnera, který odpovídá na položku, která má PNRP ID, která nejvíce odpovídá implementované cíl ID PNRP. Uzel, který obdrží zprávu požadavku PNRP prozkoumá vlastní mezipaměti a provede následující akce:  
  
-   Je-li PNRP ID najde, odpoví sdílené požadovaný koncový bod přímo na vyžádání partnera.  
  
-   Pokud nebylo nalezeno PNRP ID a s ID PNRP v mezipaměti bude co nejblíže ke PNRP ID cíle, požadované sdílené odešle odpověď na vyžádání partnera obsahující adresu IPv6 partnerského uzlu, který představuje položku s ID PNRP, které přesněji odpovídá cílovému ID PNRP. Pomocí IP adresy v odpovědi, odešle požadovaného uzlu další žádosti PNRP zprávu na adresu IPv6 reagovat nebo zkontrolujte své mezipaměti.  
  
-   Pokud nebylo nalezeno PNRP ID a není k dispozici žádné ID PNRP ve své mezipaměti, který je blíž ke PNRP ID cíle, odešle požadované sdílené žádajícího sdílené odpovědi, která upozorňuje na tento stav. Vyžádání sdílené potom Vybere nejbližší PNRP ID.  
  
-  
  
 Vyžádání sdílené tento proces pokračuje s po sobě následující iterace, nakonec vyhledání uzlu, který zaregistrované ID PNRP.  
  
 V rámci <xref:System.Net.PeerToPeer> obor názvů, je vztah m: n mezi <xref:System.Net.PeerToPeer.PeerName> záznamy, které obsahují koncových bodů a cloudy PNRP nebo skupiny uzlů, ve kterých komunikují. Pokud je duplicitní nebo zastaralé položky nebo více uzlů se stejným názvem sdílené, PNRP uzly můžete získat aktuální informace o použití <xref:System.Net.PeerToPeer.PeerNameResolver> třídy. <xref:System.Net.PeerToPeer.PeerNameResolver> Metody použití název jednoho partnera ke zjednodušení perspektivy záznamy název jedné sdílené peer m a k témuž partnerovi jeden pro mnoho cloudů. Toto je podobná dotaz provádí pomocí spojení relační tabulky. Po úspěšném dokončení zpracování vrátí objekt překladače <xref:System.Net.PeerToPeer.PeerNameRecordCollection> pro název zadaný partnera.  Například název partnerského zařízení by tomu bylo ve všech záznamech název sdílené v kolekci, seřazené podle cloudu. Toto jsou instance název partnerského zařízení, jehož podpůrné data mohou být vyžádány aplikace na základě PNRP.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer>

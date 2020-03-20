---
title: Publikování a řešení názvů partnerských uzlů
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 4a0787972a61f5700d1e8728be96db8ef9ee749e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623204"
---
# <a name="peer-name-publication-and-resolution"></a>Publikování a řešení názvů partnerských uzlů

## <a name="publishing-a-peer-name"></a>Publikování názvu partnera  

 Chcete-li publikovat nové ID PNRP, partner provede následující:  
  
- Odešle zprávy publikace PNRP svým sousedům mezipaměti (protějškům, kteří zaregistrovali ID PNRP v nejnižší úrovni mezipaměti) do osiva jejich mezipamětí.  
  
- Vybere náhodné uzly v cloudu, které nejsou jeho sousedy a odešle jim PNRP požadavky na překlad názvů pro své vlastní ID P2P. Výsledný proces určení koncového bodu zasílá mezipaměti náhodných uzlů v cloudu s ID PNRP publikujícího partnera.  
  
Uzly PNRP verze 2 nepublikují ID PNRP, pokud řeší pouze jiná ID P2P. Hodnota registru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 (typ REG_DWORD) určuje, že partneři používají pnrp pouze pro překlad názvů, nikdy pro publikování názvů. Tuto hodnotu registru lze také nakonfigurovat prostřednictvím zásad skupiny.  
  
## <a name="resolving-a-peer-name"></a>Řešení názvu partnera

 Vyhledání dalších partnerů v síti nebo cloudu PNRP je proces složený ze dvou fází:  
  
1. Stanovení koncového bodu  
  
2. ID PNRP rozlišení  
  
 Ve fázi určení koncového bodu druhá strana, která se pokouší vyřešit ID PNRP služby v jiném počítači, určuje adresu IPv6 tohoto vzdáleného partnera.  Vzdálený partner je ten, který publikoval nebo je přidružen k ID PNRP počítače nebo služby.  
  
 Po potvrzení, že vzdálený koncový bod byl zaregistrován do cloudu PNRP, žádající partner ve fázi rozlišení PNRP ID odešle požadavek na tento koncový bod partnera pro ID PNRP požadované služby. Koncový bod odešle odpověď potvrzující ID PNRP služby, komentář a až 4 kilobajty další informace, které může žádající partner použít pro budoucí komunikaci. Pokud je například požadovaným koncovým bodem herní server, mohou další data záznamu jmen partnera obsahovat informace o hře, úrovni hry a aktuálním počtu hráčů.  
  
 Ve fázi stanovení koncového bodu Používá PNRP iterativní proces pro vyhledání uzlu, který publikoval ID PNRP, ve kterém uzel provádějící rozlišení je zodpovědný za kontaktování uzlů, které jsou postupně blíže k cílovéi ID PNRP.  
  
 Chcete-li provést překlad názvů v PNRP, partner zkontroluje položky ve své vlastní mezipaměti pro položku, která odpovídá cílovému ID PNRP. Pokud je nalezen, peer odešle zprávu žádosti PNRP peer a čeká na odpověď. Pokud není nalezena položka pro ID PNRP, druhá strana odešle zprávu požadavku PNRP druhé straně, která odpovídá položce, která má ID PNRP, které nejvíce odpovídá cílovému ID PNRP. Uzel, který obdrží zprávu požadavku PNRP, zkontroluje vlastní mezipaměť a provádí následující akce:  
  
- Pokud je nalezeno ID PNRP, požadovaný koncový bod peer odpovědi přímo na žádající peer.  
  
- Pokud ID PNRP není nalezen a ID PNRP v mezipaměti je blíže k cílové ID PNRP, požadovaný partner odešle odpověď na žádající partner obsahující adresu IPv6 partnera, který představuje položku s ID PNRP, který více odpovídá cílové ID PNRP. Pomocí adresy IP v odpovědi odešle žádající uzel na adresu IPv6 další zprávu požadavku PNRP, aby odpověděl nebo prozkoumal její mezipaměť.  
  
- Pokud ID PNRP není nalezen a není žádné PNRP ID v mezipaměti, která je blíže k cílové ID PNRP, požadovaný partner odešle žádající peer odpověď, která označuje tuto podmínku. Žádající partner pak zvolí nejbližší ID PNRP.  
  
Žádající partner pokračuje v tomto procesu s po sobě jdoucími iterací, případně lokalizovat uzel, který zaregistroval ID PNRP.  
  
 V <xref:System.Net.PeerToPeer> rámci oboru názvů existuje vztah N:N <xref:System.Net.PeerToPeer.PeerName> mezi záznamy, které obsahují koncové body a cloudy PNRP nebo sítě, ve kterých komunikují. Pokud existují duplicitní nebo zastaralé položky nebo více uzlů se stejným názvem partnera, mohou <xref:System.Net.PeerToPeer.PeerNameResolver> uzly PNRP získat aktuální informace pomocí třídy. Metody <xref:System.Net.PeerToPeer.PeerNameResolver> používají jeden název partnera pro zjednodušení perspektivy na jeden peer-to-many peer name records a stejný jeden peer to many cloud. To je podobné dotazu prováděnému pomocí spojení relační tabulky. Po úspěšném dokončení resolver <xref:System.Net.PeerToPeer.PeerNameRecordCollection> objekt vrátí pro zadaný název partnera.  Například název partnera by dojít ve všech záznamů názvu partnera v kolekci, seřazené podle cloudu. Jedná se o instance názvu partnera, jehož podpůrná data mohou být požadována aplikací založenou na PNRP.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer>

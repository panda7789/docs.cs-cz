---
title: Publikování a řešení názvů partnerských uzlů
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 330117e103f7729ecf6f18ff551f65f1ba0f35da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642097"
---
# <a name="peer-name-publication-and-resolution"></a>Publikování a řešení názvů partnerských uzlů

## <a name="publishing-a-peer-name"></a>Publikování název partnerského zařízení  

 Chcete-li publikovat nové ID PNRP, partnerské zařízení provede následující akce:  
  
- Odešle zprávy publikace PNRP k jejím sousedům mezipaměti (partnerské uzly, které jste zaregistrovali ID PNRP na nejnižší úrovni mezipaměti) naplnit jejich mezipamětí.  
  
- Zvolí náhodné uzly v cloudu, které nejsou jeho okolím a odesílá požadavky na řešení PNRP název pro vlastní ID P2P. Výsledný procesu určení koncový bod nasazení nasazuje mezipamětí náhodné uzly v cloudu s ID PNRP publikování partnerského uzlu.  
  
PNRP verze 2 uzly nepublikujte ID PNRP, pokud jsou pouze řeší jiné ID P2P. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly = 1 hodnotu registru (typ REG_DWORD) určuje, zda partnerské uzly protokolu PNRP pouze používat pro překlad názvů, nikdy pro název publikace. Tato hodnota registru je také možné nakonfigurovat pomocí zásad skupiny.  
  
## <a name="resolving-a-peer-name"></a>Název partnera řešení

 Vyhledání dalších partnerských uzlů v PNRP sítě nebo cloudové je proces se skládá ze dvou fází:  
  
1. Určení koncového bodu  
  
2. ID řešení PNRP  
  
 Ve fázi stanovení koncový bod partnerského uzlu, který se pokouší se přeložit ID PNRP služby na jiném počítači určuje adresu protokolu IPv6 tohoto vzdáleného partnerského uzlu.  Vzdáleném partnerském je ta, kterou publikována nebo je přidružen ID PNRP počítače nebo služby.  
  
 Po potvrzení, že vzdálený koncový bod byl zaregistrován do cloudu PNRP, žádost o partnerským zařízením ve fázi překladu PNRP ID odešle žádost do tohoto koncového bodu partnera pro ID PNRP požadované služby. Koncový bod pošle odpověď. potvrzení ID PNRP služby komentář, a až 4 kB dalších informací, že žádosti o vytvoření partnerského vztahu můžete použít pro budoucí komunikaci. Například pokud požadovaný koncový bod serveru hry, data další peer název záznamu může obsahovat informace o hry, úroveň play a aktuální počet hráčů.  
  
 PNRP ve fázi stanovení koncový bod používá iterativní proces pro vyhledání uzlu, která publikuje ID PNRP, ve které je zodpovědný za kontaktování uzly, které jsou postupně blíž k cílové ID PNRP. uzel vyřešení  
  
 Provádět překlad adres v PNRP byly partnerské prozkoumá položky vlastní mezipaměti pro položku, která odpovídá cílové ID PNRP. Pokud najde, partnerský uzel odešle zprávu požadavku PNRP partnerským zařízením a čeká na odpověď. Pokud není nalezen záznam pro PNRP ID, partnerský uzel odešle zprávu požadavku protokolu PNRP na partnera, který odpovídá položce, která má ID PNRP, který nejlépe odpovídá cílové ID PNRP. Uzel, který obdrží zprávu požadavku PNRP prozkoumá svoji vlastní mezipaměti a provede následující akce:  
  
- Pokud je nalezeno PNRP ID, požadovaný koncový bod partnera odpovědi přímo na vyžádání partnera.  
  
- Pokud nebylo nalezeno PNRP ID a ID PNRP v mezipaměti je blíž ke cílové PNRP ID, požadované sdílené odešle odpověď na žádost o partnera obsahující IPv6 adresu partnerského uzlu, který představuje položku s ID PNRP, která lépe odpovídá cílovému ID PNRP. Pomocí IP adresy v odpovědi, odešle žádost o uzlu další zprávu požadavku protokolu PNRP na adresu IPv6 a odpověď nebo zkontrolovat uloženou v mezipaměti.  
  
- Pokud nebylo nalezeno PNRP ID a neexistuje žádné ID PNRP v mezipaměti, který je blíž k cíli PNRP ID, požadované sdílené odešle žádost o peer odpověď, která upozorňuje na tento stav. Žádost o peer potom Vybere nejbližší ID PNRP.  
  
Žádost o peer tento proces pokračuje s každou následnou iterací, nakonec vyhledání uzel, který zaregistrované ID protokolu PNRP.  
  
 V rámci <xref:System.Net.PeerToPeer> obor názvů, existuje vztah n: n mezi <xref:System.Net.PeerToPeer.PeerName> záznamy, které obsahují koncové body a cloudy PNRP nebo OK, ve kterých komunikovat. Pokud existují duplicitní nebo zastaralý položky nebo více uzlů se stejným názvem sdílené, PNRP uzly můžete získat pomocí aktuální informace <xref:System.Net.PeerToPeer.PeerNameResolver> třídy. <xref:System.Net.PeerToPeer.PeerNameResolver> Metody používají název jednoho partnerského zařízení ke zjednodušení perspektivu pro záznamy názvového jedné sdílené peer m a témuž jeden na mnoho cloudů. Toto je podobný dotaz provádí spojení relační tabulky. Po úspěšném dokončení vrátí objekt překladače <xref:System.Net.PeerToPeer.PeerNameRecordCollection> pro název zadaného partnera.  Název partnerského zařízení by tomu bylo ve všech záznamech název partnera v kolekci, například seřazené podle cloudu. Toto jsou instance název partnerského zařízení, jehož podpůrné data mohou být vyžádány aplikací založené na protokolu PNRP.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer>

---
title: Mezipaměti PNRP
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 3ed3e11e702c8933b500421de5654b212cdd80d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64622993"
---
# <a name="pnrp-caches"></a>Mezipaměti PNRP
Peer Name Resolution Protocol (PNRP) mezipaměti jsou místní kolekce algoritmicky vybraných koncových bodů rovnocenných souborů udržovaných na druhé straně.  
  
## <a name="pnrp-cache-initialization"></a>Inicializace mezipaměti PNRP  
 Chcete-li inicializovat mezipaměť PNRP nebo kolekci záznamů jmen partnera při spuštění partnerského uzlu, uzel může použít následující metody:  
  
- Trvalé položky mezipaměti, které byly přítomny při vypnutí uzlu, jsou načteny z úložiště pevného disku.  
  
- Pokud aplikace používá infrastrukturu spolupráce P2P, informace o spolupráci jsou k dispozici ve Správci kontaktů pro tento uzel.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Změna velikosti rezoluce názvů partnera pomocí víceúrovňové mezipaměti  
 Chcete-li zachovat velikosti mezipamětí PNRP malé, partnerské uzly používají víceúrovňovou mezipaměť, ve které každá úroveň obsahuje maximální počet položek. Každá úroveň v mezipaměti představuje o desetinu menší část číselného místa ID PNRP (2<sup>256).</sup> Nejnižší úroveň v mezipaměti obsahuje místně registrované ID PNRP a další ID PNRP, které jsou číselně blízko. Jako úroveň mezipaměti je vyplněna maximálně 20 položek, je vytvořena nová nižší úroveň. Maximální počet úrovní v mezipaměti je v pořadí log10(Celkový počet ID PNRP v cloudu). Například pro globální cloud se 100 miliony ID PNRP nejsou v mezipaměti více než 8 (=log10(100 000 000)) a podobný počet směrování k vyřešení ID PNRP během překladu názvů. Tento mechanismus umožňuje distribuované hash tabulky, pro které lze vyřešit libovolné ID PNRP předáním zprávy PNRP požadavku na nejbližší partner, dokud peer s odpovídající CPA je nalezen.  
  
 Chcete-li zajistit, že rozlišení může dokončit, pokaždé, když uzel přidá položku na nejnižší úroveň své mezipaměti, zaplaví kopii položky do všech uzlů v rámci poslední úrovně mezipaměti.  
  
 Položky mezipaměti jsou aktualizovány v průběhu času. Položky mezipaměti, které jsou zastaralé, jsou odebrány z mezipaměti. Výsledkem je, že distribuovaná tabulka hash ID PNRP je založena na aktivních koncových bodech, na rozdíl od DNS, ve kterém záznamy adres a protokol DNS neposkytují žádnou záruku, že uzel přidružený k adrese je aktivně v síti.  
  
## <a name="other-pnrp-caches"></a>Další mezipaměti PNRP  
 Dalším trvalým úložištěm dat je místní mezipaměť.  Kromě ostatníobjekty potřebné pro aktivitu PNRP může zahrnovat záznamy spojené s cloudem PNRP nebo relace spolupráce, která je bezpečně publikována a synchronizována mezi všemi členy cloudu. Toto replikované úložiště představuje zobrazení dat skupiny, která by měla být stejná pro všechny členy skupiny. Technicky tyto objekty nejsou záznamy jako takové, ale spíše aplikace, přítomnost a data objektu určené pro místní mezipaměti. Použití cloudu PNRP zajišťuje, že objekty jsou šířeny do všech uzlů v relaci spolupráce nebo Cloud PNRP.  Záznam replikace mezi členy cloudu používá SSL k zajištění šifrování a integrity dat.  
  
 Když se partner připojí ke cloudu, automaticky neobdrží data místní mezipaměti z partnerského partnera hostitele, ke kterému se připojují; musí se přihlásit k odběru partnerského partnera hostitele, aby mohli přijímat aktualizace v aplikacích, přítomnosti a objektových datech. Po počáteční synchronizaci partneři pravidelně synchronizují replikovaná úložiště, aby zajistili, že všichni členové skupiny mají konzistentně stejné zobrazení.  Relaci spolupráce nebo aplikace v rámci relace spolupráce může také provádět stejnou funkci.  
  
 Po zahájení relace spolupráce pro cloud, aplikace můžete zaregistrovat partnery a začít publikovat jejich informace pomocí zabezpečení definovaného rozsahem cloudu. Když se druhá strana připojí ke cloudu, mechanismy zabezpečení pro cloud se použijí na druhou úroveň, což mu dává obor, ve kterém se má účastnit.  Jeho záznamy pak mohou být bezpečně publikovány v rámci cloudu. Všimněte si, že rozsah cloudu nemusí být stejný jako rozsah aplikace spolupráce.  
  
 Partneři mohou zaregistrovat zájem o příjem objektů od jiných partnerů. Při aktualizaci objektu je aplikace pro spolupráci upozorněna a nový objekt je předán všem odběratelům aplikace. Například partner v aplikaci skupinového chatu může zaregistrovat zájem o příjem informací o aplikaci, které mu odešlou všechny záznamy chatu jako data aplikace.  To mu umožňuje sledovat aktivitu chatu v cloudu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer>

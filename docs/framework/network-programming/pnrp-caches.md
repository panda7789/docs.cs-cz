---
title: "Mezipamětí PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dc9476b546ea55234c536a34416efc2bff0166de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-caches"></a>Mezipamětí PNRP
Sdílené mezipaměti protokolu PNRP (Name Resolution) jsou místní kolekce koncových bodů algorithmically vybrané sdílené udržovaný na partnerský uzel.  
  
## <a name="pnrp-cache-initialization"></a>Inicializace mezipaměti PNRP  
 K chybě při inicializaci mezipaměti PNRP nebo sdílené název záznamu kolekce, při spuštění uzlu sdílené, uzlu můžete použít následující metody:  
  
-   Trvalá mezipaměť položky, které byly při ukončení uzlu se načítají z úložiště pevný disk.  
  
-   Pokud aplikace používá infrastrukturu P2P spolupráce, spolupráce informace jsou k dispozici v obraťte se na správce pro tento uzel.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Škálování Peer Name Resolution s víceúrovňovou mezipaměti  
 Pokud chcete zachovat velikosti mezipaměti PNRP malý, použijte partnerské uzly víceúrovňovou mezipaměti, ve kterém každá úroveň obsahuje maximální počet položek. Každou úroveň v mezipaměti představuje jednu desetinu menší část místa číslo PNRP ID (2<sup>256</sup>). Nejnižší úrovni v mezipaměti obsahuje místně registrovaných ID PNRP a jiné PNRP ID, který podle čísel blíží ho. Jako úroveň mezipaměti je vyplněn maximálně 20 položek, vytvoří se nový nižší úrovni. Maximální počet úrovní v mezipaměti, které je v řádu log10 (celkový počet ID PNRP v cloudu). Například pro globální cloudu s ID 100 miliónů PNRP, existují maximálně 8 (=log10(100,000,000)) úrovně v mezipaměti a podobné počet skoků přeložit PNRP ID při překladu. Tento mechanismus umožňuje distribuované zatřiďovací tabulku, pro které mohou být vyřešeny libovolný ID PNRP předávání zpráv PNRP požadavku na nejbližší partnera, dokud nebude nalezen partnera s odpovídající CPA.  
  
 K zajištění toho, zda řešení dokončí, pokaždé, když uzel přidá položku do nejnižší úroveň své mezipaměti ho floods kopii položky pro všechny uzly v rámci poslední úroveň mezipaměti.  
  
 Položky mezipaměti se aktualizuje v čase. Položky mezipaměti, které jsou zastaralé, se odeberou z mezipaměti. Výsledkem je, že distribuované zatřiďovací tabulku PNRP ID je založen na aktivní koncových bodů, na rozdíl od DNS, ve kterém záznamy adres a protokol DNS poskytují zaručeno, že uzel přidružené k adrese je aktivně v síti.  
  
## <a name="other-pnrp-caches"></a>Další mezipamětí PNRP  
 Jiného úložiště dat je místní mezipaměti.  Kromě jiných objektů pro činnost PNRP může zahrnovat záznamy související s PNRP cloud nebo spolupráce relaci, která je bezpečně publikována a synchronizovat mezi všechny členy cloudu. Toto replikované úložiště představuje zobrazení dat skupiny, které by měly být stejné pro všechny členy skupiny. Technicky tyto objekty nejsou záznamy samo o sobě, ale místo aplikace, stavu a dat objektů, které jsou určené pro místní mezipaměti. Při používání cloudových PNRP zajistí, že všechny uzly v relaci spolupráce nebo v cloudu PNRP rozšířeny objekty.  Záznam replikace mezi členy cloudu používá k šifrování a integritu dat protokol SSL.  
  
 V případě sdílené připojen do cloudu, nemá žádné automaticky místní mezipaměti dat od hostitele partnera, ke kterému jsou připojit; mají k odběru na hostitele partnera a získat aktualizace v aplikaci, stavu a data objektu. Po počáteční synchronizaci synchronizaci partnerské uzly pravidelně jejich replikované úložiště zajistěte, aby všechny členy skupiny konzistentně jediného zobrazení.  Spolupráce relace nebo aplikace v rámci relace spolupráce může také provádí stejnou funkci.  
  
 Po zahájení relace spolupráce pro cloud, aplikace můžete zaregistrovat partnerské uzly a začít publikování své informace pomocí zabezpečení definované obor cloudu. Když sdílené připojí do cloudu, použijí se na partnera, která poskytuje obor, ve kterém se zúčastnit mechanismy zabezpečení pro cloud.  Jeho záznamy lze publikovat v rámci oboru cloudu pak bezpečně. Poznámka: obor cloudu nemusí být stejný jako spolupráce oboru aplikace.  
  
 Požadavky na příjem objekty z dalších partnerských uzlů můžete zaregistrovat partnerské uzly. Při aktualizaci objektu, je upozornění aplikace spolupráce a nový objekt předaný všechny odběratele aplikace. Partnerského uzlu v aplikaci konverzace skupiny můžete například zaregistrovat zájem o přijetí informací o aplikaci, která se odešle všechny záznamy chat za data aplikací.  To umožňuje sledovat činnost chat v rámci cloudu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer>

---
title: Mezipaměti PNRP
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 9cd1901e716cab9f1b47825a5d3ecdb071a58440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975270"
---
# <a name="pnrp-caches"></a>Mezipaměti PNRP
Sdílené mezipaměti protokolu PNRP (Name Resolution) jsou místní kolekce koncových bodů algorithmically vybrané sdílené udržuje na partnerský uzel.  
  
## <a name="pnrp-cache-initialization"></a>Inicializace mezipaměti PNRP  
 Inicializace mezipaměti PNRP nebo Peer název záznamu kolekce, při spuštění partnerský uzel, uzel můžete použít následující metody:  
  
-   Trvalá mezipaměť položky, které byly k dispozici, pokud byl vypnutý uzel se načítají z úložiště na pevném disku.  
  
-   Pokud aplikace používá infrastrukturu P2P spolupráce, spolupráce informace jsou k dispozici v Správce kontaktů pro tento uzel.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Škálování Peer Name Resolution s více úrovně mezipaměti  
 Pokud chcete zachovat velikosti mezipaměti PNRP malý, použijte partnerské uzly na více mezipamětí, ve kterém každá úroveň obsahuje maximální počet položek. Každá úroveň v mezipaměti představuje desetina menší část prostoru číslo PNRP ID (2<sup>256</sup>). Nejnižší úrovni v mezipaměti obsahuje místně registrované ID PNRP a jiné ID PNRP, které jsou číselně blízko ho. Jako úroveň mezipaměti je vyplněna maximálně 20 položek, vytvoří se nové nižší úrovni. Maximální počet úrovní v mezipaměti je v řádu log10 (celkový počet ID PNRP v cloudu). Například pro globálního cloudu s ID 100 milionů PNRP, nejsou maximálně 8 (=log10(100,000,000)) úrovně v mezipaměti a podobně jako počet segmentů směrování se přeložit PNRP ID během překladu názvů. Tento mechanismus umožňuje distribuovaná zatřiďovací tabulku, pro který dá vyřešit libovolného ID PNRP přesměrovací zprávy s požadavkem na protokolu PNRP na nejbližší partnera, dokud nebude nalezen partnera s odpovídající CPA.  
  
 K zajištění, zda rozlišení dokončí, pokaždé, když uzel přidá položku do nejnižší úroveň mezipaměti, ho floods kopii položky pro všechny uzly v rámci poslední úroveň mezipaměti.  
  
 Položky mezipaměti se aktualizují v čase. Položky mezipaměti, které jsou zastaralé, jsou odebrány z mezipaměti. Výsledkem je, že je distribuovaná zatřiďovací tabulku ID PNRP podle aktivní koncové body, na rozdíl od DNS, ve kterém záznamy adres a protokolu DNS poskytují žádná záruka, že uzel přidružené k adresám je aktivně v síti.  
  
## <a name="other-pnrp-caches"></a>Jiných mezipaměti PNRP  
 Jiného úložiště trvalých dat se o místní mezipaměti.  Kromě jiných objektů potřebných pro aktivitu protokolu PNRP může obsahovat záznamy související s PNRP cloudu nebo spolupráci relace, který je bezpečně publikovat a synchronizaci mezi všemi členy v cloudu. Toto replikované úložiště představuje zobrazení dat skupiny, které by se měly stejný pro všechny členy skupiny. Technicky vzato tyto objekty nejsou záznamy samo o sobě, ale místo toho aplikace, přítomnost a datový objekt určený pro místní mezipaměti. Použití cloudu PNRP zajišťuje, že objekty se rozšíří do všech uzlů v relaci spolupráce nebo v cloudu PNRP.  Záznam replikace mezi členy cloudu používá protokol SSL pro šifrování a integritu dat.  
  
 Poté, co partnerský uzel připojí do cloudu, nedostávají automaticky data z místní mezipaměti od partnera hostitele, ke kterému jsou připojit; mají k odběru na hostitele partnera a získat aktualizace v aplikaci, prezentace a data objektu. Po počáteční synchronizaci partnerské uzly pravidelně synchronizovat své replikované úložiště Ujistěte se, že všichni členové skupiny konzistentně stejného zobrazení.  Spolupráce relace nebo aplikace v rámci relace spolupráci mohou také provádět má stejnou funkci.  
  
 Po relaci spolupráce pro cloud, můžete aplikace zaregistrovat partnerské uzly a začněte publikováním svých informací pomocí zabezpečení určené obor cloudu. Poté, co partnerský uzel připojí do cloudu, bezpečnostní mechanismy pro cloud se použijí na partnera, že mu poskytneme oboru, ve kterém se zúčastnit.  Záznamy můžete publikovat v rámci oboru cloudu pak bezpečně. Mějte na paměti, obor cloudu nemusí být stejné jako spolupráci oboru aplikace.  
  
 Partnerské uzly můžete zaregistrovat zájem přijímají se objekty z dalších partnerských uzlů. Při aktualizaci objektu spolupráci aplikaci zasláno oznámení a nový objekt je předán všichni předplatitelé aplikace. Sdílené ve skupině chatovací aplikaci můžete například zaregistrovat zájem příjem informací o aplikaci, která pošle ho všechny konverzace záznamy jako data aplikací.  Umožní vám to sledovat činnost chat v rámci cloudu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer>

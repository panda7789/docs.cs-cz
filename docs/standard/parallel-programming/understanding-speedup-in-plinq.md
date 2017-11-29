---
title: "Porozumění zrychlení v PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3373cb6a2c535bd7d42eb062e1f9727952f7cfb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-speedup-in-plinq"></a>Porozumění zrychlení v PLINQ
Primárním účelem PLINQ je pro urychlení provádění LINQ na objekty dotazy spuštěním dotazu delegáty paralelně na počítačích s více jádry. Při zpracování jednotlivých prvků ve zdrojové kolekci je nezávislé, bez sdíleného stavu související se situací mezi jednotlivé delegáty se nejlépe provádí PLINQ. Tyto operace jsou obvyklé v technologii LINQ to objekty a PLINQ a se často nazývají "*delightfully paralelní*" vzhledem k tomu, že je to možné snadno plánování na více vláken. Nicméně ne všechny dotazy skládat delightfully paralelních operací; ve většině případů dotazu zahrnuje některé operátory buď nesmí být paralelizovaná málo, nebo které zpomalit paralelní provádění. A dokonce i s dotazy, které jsou zcela delightfully paralelní, musí PLINQ stále oddílu zdroj dat a plánování práce na vláken a obvykle sloučení výsledků po dokončení dotazu. Všechny tyto operace přidání do výpočetní náklady paralelizace; Tyto náklady přidávání paralelizace se nazývají *režijní náklady na*. Cílem je dosáhnout optimálního výkonu v PLINQ dotazu, maximalizovat částí, které jsou delightfully paralelní a minimalizovat částí, které vyžadují režijní náklady. Tento článek obsahuje informace, které vám pomohou psát dotazy PLINQ, které jsou co nejúčinnější při stále vracet správné výsledky.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Faktory, které mají vliv na výkon dotazu PLINQ  
 V následujících částech jsou uvedeny některé nejdůležitější faktorů, že dopad výkon paralelního dotazu. Jedná se o Obecné příkazy, které samy o sobě nejsou dostatečná k předvídání výkon dotazů ve všech případech. Jako vždy je důležité k měření skutečným výkonem konkrétní dotazů na počítačích s rozsahem reprezentativní konfigurace a zatížení.  
  
1.  Výpočetní náklady na celkový práce.  
  
     K dosažení zrychlení, musí mít dotazu PLINQ dostatek delightfully paralelní práce k posunutí režijní náklady. Práce může být vyjádřený jako výpočetní náklady na každý delegáta násobí hodnotou počet elementů ve zdrojové kolekci. Za předpokladu, že operace může být paralelizovaná málo, čím výpočetně nákladné je, tím větší možnost pro zrychlení. Například pokud funkci přijímá jeden milisekund k provedení, může trvat sekvenční dotazu více než 1000 elementy bude trvat jednu sekundu k provedení této operace, zatímco paralelní dotaz na počítači s čtyři jader pouze 250 milisekund. Dostaneme zrychlení 750 milisekund. V případě potřeby sekundu provést pro každý prvek funkce by být zrychlení 750 sekund. Pokud delegát je velmi náročná, může PLINQ nabízí významné zrychlení s pouze několik položek ve zdrojové kolekci. Naopak malé zdroj kolekce s trivial delegáti nejsou obvykle vhodnými kandidáty pro PLINQ.  
  
     V následujícím příkladu je queryA pravděpodobně vhodným kandidátem pro PLINQ, za předpokladu, že jeho vyberte funkce zahrnuje značné úsilí. queryB je pravděpodobně není vhodným kandidátem, protože není k dispozici dostatek pracovních v příkazu Select a režii paralelizace bude posunut většinu nebo všechny zrychlení.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2.  Počet logických jádra systému (stupně paralelního zpracování).  
  
     Tento bod je zřejmé důsledkem v předchozí části, dotazy, které jsou delightfully paralelní rychleji, na počítače s více jader protože práce je možné rozdělit mezi více souběžných vláken. Celkové množství zrychlení závisí na to, jaké procento celkové práce dotazu je může běžet paralelně. Ale Nepředpokládejte, že všechny dotazy se spustí dvakrát jako rychlé v počítači osm jader jako čtyři základní počítač. Při ladění dotazy pro optimální výkon, je důležité k měření skutečné výsledky na počítačích s různým počtem jader. Tento bod má vztah k bodu #1: větších datových sad jsou nutné k využít větší výpočetní prostředky.  
  
3.  Počet a typ operací.  
  
     PLINQ poskytuje AsOrdered operátor pro situace, ve kterých je potřeba udržovat pořadí elementů ve zdrojové sekvence. Náklady spojené s řazení, ale je obvykle mírné tyto poplatky. Operace GroupBy a připojení k podobně zpoplatněná režijní náklady. PLINQ poskytuje nejlepší výkon, pokud je povoleno pro zpracování elementů ve zdrojové kolekci v libovolném pořadí a předat další operátor, jakmile jsou připravené. Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  Formulář spuštění dotazu.  
  
     Pokud ukládáte voláním ToArray nebo ToList výsledků dotazu, musí být výsledky ze všech paralelních vláken sloučeny do jednoho datového struktury. To zahrnuje výpočetní nákladů na nevyhnutelné použít. Podobně pokud jste výsledky iteraci pomocí příkazu foreach (pro každou v jazyce Visual Basic) smyčky, výsledků pracovních vláken muset serializovat do vlákno enumerátor. Ale pokud chcete provést některé akce na základě výsledku z každé vlákno, můžete použít metodu ForAll pro práci na více vláken.  
  
5.  Typ možností sloučení.  
  
     PLINQ lze nakonfigurovat buď jeho výstupní vyrovnávací paměť a ho vytvořit bloky dat nebo všechny najednou, po celou sadu výsledků vytváří, nebo jednotlivé výsledky datového proudu jako se vytváří. Bývalé výsledkem je ke snížení celkové čas spuštění a druhá možnost vede ke snížení latence mezi poskytuje elementy.  Při možností sloučení nemají vždy významný vliv na celkový výkon dotazů, můžou ovlivnit dosahovaný výkon protože budou řídit, jak dlouho uživatel musí počkat a zobrazte výsledky. Další informace najdete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  Druh rozdělení do oddílů.  
  
     V některých případech může způsobit dotazu PLINQ přes kolekci indexovanou zdroje nevyváženou pracovní zatížení. V takovém případě je možné zvýšit výkon dotazů tak, že vytvoříte vlastní dělicí metody. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Když PLINQ zvolí sekvenční režimu  
 PLINQ se vždy pokusí o spuštění dotazu alespoň tak rychlý jako dotaz se spouští sekvenčně. I když PLINQ zdá o tom, jak u nákladné delegáty uživatele, nebo jak velkou vstupního zdroje, vyhledejte určité dotazu "tvarů." Konkrétně vypadá pro operátory dotazu nebo kombinace operátory, které obvykle způsobí dotazu na provedení pomaleji v paralelním režimu. Pokud najde takové tvarů, PLINQ ve výchozím nastavení přejde zpět do sekvenční režimu.  
  
 Ale po měření výkonu konkrétní dotaz, může určit, že ve skutečnosti běží rychleji v paralelním režimu. V takových případech můžete použít <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> příznak prostřednictvím <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda k vynucení PLINQ paralelní dotaz. Další informace najdete v tématu [postupy: určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Následující seznam popisuje tvary dotazu, které PLINQ ve výchozím nastavení bude vykonán v sekvenčním režimu:  
  
-   Dotazy, které obsahují s výběrem indexované kde indexované označit více, nebo klauzuli ElementAt po řazení nebo filtrování operátor, který se má odebrat nebo změně uspořádání původní indexy.  
  
-   Dotazy obsahující proveďte TakeWhile, přeskočit, SkipWhile – operátor a kde indexy ve zdrojové sekvence nejsou ve stejném pořadí.  
  
-   Dotazy, které obsahují Zip nebo SequenceEquals, pokud se některý ze zdrojů dat má indexu původně seřazené a jiný zdroj dat je indexovanou (tj. pole nebo IList(T)).  
  
-   Dotazy, které obsahují Concat, pokud je tato indexovanou datové zdroje.  
  
-   Dotazy, které obsahují vrátit, pokud se použije ke zdroji dat indexovanou.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

---
title: Porozumění zrychlení v PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
ms.openlocfilehash: 07b5027d560a4caccc6c0a516c3f70c11df6be83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139902"
---
# <a name="understanding-speedup-in-plinq"></a>Porozumění zrychlení v PLINQ
Primárním účelem PLINQ je urychlit provádění linq na objekty dotazů spuštěním delegáty dotazu paralelně na vícejádrových počítačích. PLINQ funguje nejlépe při zpracování každého prvku ve zdrojové kolekci je nezávislý, bez sdíleného stavu zapojených mezi jednotlivé delegáty. Tyto operace jsou běžné v LINQ na objekty a PLINQ a jsou často nazývány "*nádherně paralelní*", protože se snadno hodí k plánování na více vláknech. Ne všechny dotazy se však skládají výhradně z nádherně paralelních operací; ve většině případů dotaz zahrnuje některé operátory, které buď nelze paralelizovat, nebo které zpomalují paralelní spuštění. A i s dotazy, které jsou zcela nádherně paralelní, PLINQ musí stále rozdělit zdroj dat a naplánovat práci na vláknech a obvykle sloučit výsledky po dokončení dotazu. Všechny tyto operace přidat výpočetní náklady na paralelizaci; tyto náklady na přidání paralelizace se nazývají *režie*. Chcete-li dosáhnout optimálního výkonu v dotazu PLINQ, cílem je maximalizovat součásti, které jsou nádherně paralelní a minimalizovat součásti, které vyžadují režii. Tento článek obsahuje informace, které vám pomohou psát plinq dotazy, které jsou co nejúčinnější, zatímco stále přináší správné výsledky.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Faktory, které ovlivňují výkon dotazu PLINQ  
 V následujících částech jsou uvedeny některé nejdůležitější faktory, které ovlivňují výkon paralelních dotazů. Jedná se o obecné příkazy, které samy o sobě nestačí předpovědět výkon dotazu ve všech případech. Jako vždy je důležité měřit skutečný výkon konkrétních dotazů v počítačích s řadou reprezentativních konfigurací a zatížení.  
  
1. Výpočetní náklady na celkovou práci.  
  
     Chcete-li dosáhnout zrychlení, musí mít dotaz PLINQ dostatek nádherně paralelní práce k vyrovnání režie. Práce může být vyjádřena jako výpočetní náklady každého delegáta vynásobené počtem prvků ve zdrojové kolekci. Za předpokladu, že operace může být paralelizována, čím více je výpočtově nákladná, tím větší je příležitost pro zrychlení. Například pokud funkce trvá jednu milisekundu ke spuštění, sekvenční dotaz více než 1000 prvků bude trvat jednu sekundu k provedení této operace, zatímco paralelní dotaz v počítači se čtyřmi jádry může trvat pouze 250 milisekund. To dává zrychlení 750 milisekund. Pokud funkce vyžaduje jednu sekundu ke spuštění pro každý prvek, pak zrychlení by 750 sekund. Pokud delegát je velmi nákladné, pak PLINQ může nabídnout významné zrychlení pouze několik položek ve zdrojové kolekci. Naopak malé zdrojové kolekce s triviálnídelegáti obecně nejsou dobré kandidáty pro PLINQ.  
  
     V následujícím příkladu queryA je pravděpodobně dobrým kandidátem pro PLINQ, za předpokladu, že jeho Select funkce zahrnuje mnoho práce. queryB pravděpodobně není dobrým kandidátem, protože v příkazu Select není dostatek práce a režie paralelizace odsaze většinu nebo všechny zrychlení.  
  
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
  
2. Počet logických jader v systému (stupeň paralelismu).  
  
     Tento bod je zřejmý důsledek předchozí části, dotazy, které jsou nádherně paralelní spustit rychleji na počítačích s více jádry, protože práce může být rozdělena mezi více souběžných vláken. Celkové množství zrychlení závisí na tom, jaké procento celkové práce dotazu je paralelizovatelné. Nepředpokládejte však, že všechny dotazy budou spuštěny dvakrát rychleji v počítači s osmi jádry jako čtyřjádrový počítač. Při ladění dotazů pro optimální výkon je důležité měřit skutečné výsledky v počítačích s různým počtem jader. Tento bod souvisí s bodem #1: větší datové sady jsou nutné využít větší výpočetní prostředky.  
  
3. Počet a druh operací.  
  
     PLINQ poskytuje AsOrdered operátor pro situace, ve kterých je nutné udržovat pořadí prvků ve zdrojové sekvenci. S objednáním jsou spojeny náklady, ale tyto náklady jsou obvykle skromné. GroupBy a join operace také vznikají režii. PLINQ funguje nejlépe, když je povoleno zpracovávat prvky ve zdrojové kolekci v libovolném pořadí a předat je dalšímu operátoru, jakmile jsou připraveny. Další informace naleznete [v tématu Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Forma spuštění dotazu.  
  
     Pokud ukládáte výsledky dotazu voláním ToArray nebo ToList, musí být výsledky ze všech paralelních vláken sloučeny do jediné datové struktury. To zahrnuje nevyhnutelné výpočetní náklady. Podobně pokud iterát výsledky pomocí foreach (pro každý v jazyce Visual Basic) smyčky, výsledky z pracovních podprocesů je třeba serializovat do vlákna čítače. Ale pokud chcete provést některé akce na základě výsledku z každého vlákna, můžete použít ForAll metoda k provedení této práce na více vláken.  
  
5. Typ možností sloučení.  
  
     PLINQ lze nakonfigurovat tak, aby buď vyrovnávací paměti jeho výstup a vyrábět v blocích nebo najednou po vytvoření celé sady výsledků, nebo jinak streamovat jednotlivé výsledky, jak jsou vyráběny. První výsledky v snížení celkové doby provádění a druhý má za následek snížení latence mezi prvky výnosné.  Zatímco možnosti sloučení nemají vždy významný vliv na celkový výkon dotazu, mohou ovlivnit vnímaný výkon, protože řídí, jak dlouho musí uživatel čekat na výsledky. Další informace naleznete [v tématu Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Druh dělení.  
  
     V některých případech dotaz PLINQ přes indexovatelné zdrojové kolekce může mít za následek nevyvážené pracovní zatížení. V takovém případě může být možné zvýšit výkon dotazu vytvořením vlastního rozdělovače. Další informace naleznete [v tématu Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Když PLINQ zvolí sekvenční režim  
 PLINQ se vždy pokusí spustit dotaz alespoň tak rychle, jak by dotaz spustit postupně. Přestože PLINQ nedívá na jak výpočtově drahé delegáty uživatele jsou nebo jak velký vstupní zdroj je, přehlíží určité "tvary dotazu". Konkrétně hledá operátory dotazu nebo kombinace operátorů, které obvykle způsobí, že dotaz spustit pomaleji v paralelním režimu. Když najde takové tvary, PLINQ ve výchozím nastavení přejde zpět do sekvenčního režimu.  
  
 Však po měření výkonu konkrétní dotaz, můžete určit, že ve skutečnosti běží rychleji v paralelním režimu. V takových případech můžete <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> příznak prostřednictvím metody pokyn PLINQ paralelizovat dotaz. Další informace naleznete v [tématu How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Následující seznam popisuje obrazce dotazu, které bude ve výchozím nastavení spuštěna funkce PLINQ v sekvenčním režimu:  
  
- Dotazy, které obsahují Select, indexovány Kde, indexované SelectMany nebo ElementAt klauzule po řazení nebo filtrování operátor, který odebral nebo přeuspořádané původní indexy.  
  
- Dotazy, které obsahují Take, TakeWhile, Skip, SkipWhile operátor a kde indexy ve zdrojové sekvenci nejsou v původním pořadí.  
  
- Dotazy, které obsahují ZIP nebo SequenceEquals, pokud jeden ze zdrojů dat má původně uspořádaný index a jiný zdroj dat je indexovatelný (tj. pole nebo IList(T)).  
  
- Dotazy, které obsahují Concat, pokud se použije na indexovatelné zdroje dat.  
  
- Dotazy, které obsahují Reverse, pokud nejsou použity na indexovatelný zdroj dat.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

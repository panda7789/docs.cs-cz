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
ms.openlocfilehash: 627f1327a9fe87fc226dfbb40df50ec4855edfb9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284894"
---
# <a name="understanding-speedup-in-plinq"></a>Porozumění zrychlení v PLINQ
Hlavním účelem PLINQ je urychlení provádění LINQ to Objectsch dotazů tím, že se paralelně spouští Delegáti dotazů na vícejádrových počítačích. PLINQ provádí nejlepší, pokud je zpracování každého prvku ve zdrojové kolekci nezávislé, bez jakéhokoli sdíleného stavu mezi jednotlivými delegáty. Tyto operace jsou běžné v LINQ to Objects a PLINQ a často se nazývají "*delightfully Parallel*", protože se dají snadno naplánovat na více vláken. Ne všechny dotazy však sestávají výhradně z delightfully paralelních operací; ve většině případů dotaz zahrnuje některé operátory, které nelze buď paralelně, nebo které zpomalují paralelní spouštění. A dokonce i s dotazy, které jsou zcela delightfully paralelně, PLINQ musí stále rozdělit zdroj dat a naplánovat práci na vláknech a obvykle sloučit výsledky po dokončení dotazu. Všechny tyto operace se přidávají k výpočetním nákladům na paralelní zpracování; Tyto náklady na přidání paralelismu se nazývají *režijní*náklady. Aby bylo možné dosáhnout optimálního výkonu v PLINQ dotazu, cílem je maximalizovat části, které jsou delightfully paralelně, a minimalizovat součásti, které vyžadují režii. Tento článek poskytuje informace, které vám pomohou psát PLINQ dotazy, které jsou co nejefektivnější, a přitom stále poskytovat správné výsledky.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Faktory, které ovlivňují výkon dotazů PLINQ  
 V následujících částech jsou uvedeny některé z nejdůležitějších faktorů, které mají vliv na výkon paralelních dotazů. Jedná se o obecné příkazy, které samy o sebe nejsou dostačující pro předpověď výkonu dotazů ve všech případech. Jako vždy je důležité změřit skutečný výkon konkrétních dotazů na počítačích s řadou reprezentativních konfigurací a zatížení.  
  
1. Výpočetní náklady na celkovou práci.  
  
     Aby bylo možné dosáhnout zrychlení, musí mít PLINQ dotaz dostatek delightfully paralelní práce, aby mohl kompenzovat režii. Práci lze vyjádřit jako výpočetní náklady každého delegáta vynásobený počtem prvků ve zdrojové kolekci. Za předpokladu, že operace může být paralelně náročná, znamená to více výpočetních příležitostí, což je větší příležitost pro zrychlení. Například pokud funkce trvá jednu milisekundu, sekvenční dotaz více než 1000 prvků provede určitou operaci, zatímco paralelní dotaz na počítači se čtyřmi jádry může trvat pouze 250 milisekund. Výsledkem je 750 zrychlení milisekund. Pokud je pro každý prvek požadována funkce jedna sekunda, zrychlení by byl 750 sekund. Pokud je delegát velmi nákladný, může PLINQ nabízet významné zrychleníy s několika položkami ve zdrojové kolekci. Naopak malé zdrojové kolekce s triviálními delegáty obecně nejsou vhodnými kandidáty pro PLINQ.  
  
     V následujícím příkladu je dotazce pravděpodobně dobrým kandidátem pro PLINQ za předpokladu, že jeho funkce Select zahrnuje hodně práce. queryB je pravděpodobně nevhodný kandidát, protože v příkazu SELECT není dostatek práce a režie pro paralelní navýšení bude posunuta na většinu nebo všechny zrychlení.  
  
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
  
     Tento bod je zjevným corollaryem předchozí části, dotazy, které jsou delightfully paralelně, fungují na počítačích s více jádry, protože práci lze rozdělit mezi více souběžných vláken. Celkové množství zrychlení závisí na tom, jaké procento celkové práce dotazu je paralelizovat. Nepředpokládá se však, že všechny dotazy budou dvakrát spuštěny na osmi základních počítačích v případě čtyř základních počítačů. Při ladění dotazů na optimální výkon je důležité změřit skutečné výsledky na počítačích s různými počty jader. Tento bod se vztahuje k bodu #1: aby bylo možné využívat větší výpočetní prostředky, vyžadují se větší datové sady.  
  
3. Počet a druh operací.  
  
     PLINQ poskytuje operátor metodu AsOrdered pro situace, kdy je nutné zachovat pořadí prvků ve zdrojové sekvenci. K řazení se účtují náklady, ale tyto náklady jsou obvykle mírné. Operace GroupBy a JOIN se také účtují jako režijní náklady. PLINQ má nejlepší výkon, pokud je povoleno zpracovávat prvky ve zdrojové kolekci v libovolném pořadí a předat operátorovi Next, jakmile jsou připraveni. Další informace naleznete v tématu [pořadí zachování v PLINQ](order-preservation-in-plinq.md).  
  
4. Forma provedení dotazu.  
  
     Pokud ukládáte výsledky dotazu voláním ToArray – nebo ToList –, pak musí být výsledky ze všech paralelních vláken sloučeny do jediné datové struktury. To zahrnuje nenevyhnutelné výpočetní náklady. Podobně platí, že pokud provádíte iteraci výsledků pomocí příkazu foreach (for each Visual Basic), výsledky z pracovních vláken musí být serializovány do vlákna enumerátoru. Pokud ale chcete pouze provést určitou akci na základě výsledku z každého vlákna, můžete použít metodu ForAll k provedení této práce na více vláknech.  
  
5. Typ možností sloučení.  
  
     PLINQ se dá nakonfigurovat buď na bufferový výstup, a vytvořit ho v blocích nebo všechny najednou po vyprodukování celé sady výsledků, nebo jinak pro streamování jednotlivých výsledků při jejich tvorbě. V předchozích výsledcích se snížila celková doba spuštění a výsledkem je snížení latence mezi vydanými prvky.  I když možnosti sloučení nemají vždy zásadní dopad na celkový výkon dotazů, mohou ovlivnit vnímaný výkon, protože určují, jak dlouho musí uživatel čekat na zobrazení výsledků. Další informace naleznete v tématu [možnosti sloučení v PLINQ](merge-options-in-plinq.md).  
  
6. Druh dělení.  
  
     V některých případech může PLINQ dotaz nad indexovanou zdrojovou kolekcí způsobit nevyvážené pracovní zatížení. Pokud k tomu dojde, může být možné zvýšit výkon dotazu vytvořením vlastního rozdělovače. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Když PLINQ zvolí sekvenční režim  
 PLINQ se vždycky pokusí spustit dotaz aspoň tak rychle, protože dotaz by se spouštěl sekvenčně. I když PLINQ nevypadá na tom, jak výpočetní náklady jsou delegáti uživatelů nebo jak velké je vstupní zdroj, hledá konkrétní dotaz "tvary". Konkrétně vyhledává operátory nebo kombinace operátorů dotazů, které obvykle způsobují zpomalení dotazu v paralelním režimu. Když tyto tvary najde, PLINQ ve výchozím nastavení přejde zpět do sekvenčního režimu.  
  
 Po měření výkonu konkrétního dotazu ale můžete určit, že ve skutečnosti běží rychleji v paralelním režimu. V takových případech můžete použít <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> příznak prostřednictvím <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody pro pokyn pro PLINQ k paralelizovat dotazu. Další informace naleznete v tématu [How to: určení režimu spouštění v PLINQ](how-to-specify-the-execution-mode-in-plinq.md).  
  
 Následující seznam popisuje obrazce dotazů, které PLINQ ve výchozím nastavení spustí v sekvenčním režimu:  
  
- Dotazy, které obsahují klauzuli SELECT, Indexed WHERE, indexované operátor SelectMany nebo ElementAt za operátorem řazení nebo filtrování, který odstranil nebo přeřadí původní indexy.  
  
- Dotazy, které obsahují operátor vzít, TakeWhile –, Skip, SkipWhile – a kde indexy ve zdrojové sekvenci nejsou v původním pořadí.  
  
- Dotazy, které obsahují zip nebo SequenceEquals, pokud jeden z zdrojů dat nemá původně seřazený index a druhý zdroj dat je indexované (tj. pole nebo IList (T)).  
  
- Dotazy, které obsahují Concat, pokud nejsou aplikovány na indexované zdroje dat.  
  
- Dotazy, které obsahují reverzní, pokud nejsou aplikovány na indexovací zdroj dat.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)

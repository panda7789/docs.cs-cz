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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26128e5d707d3f331dc2b691f5a5f798bdf84c25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322989"
---
# <a name="understanding-speedup-in-plinq"></a>Porozumění zrychlení v PLINQ
Pro urychlení spuštění LINQ to Objects dotazů spuštěním dotazu delegáty paralelně na vícejádrových počítačích je primárním účelem PLINQ. PLINQ poskytuje nejlepší výkon při zpracování jednotlivých prvků ve zdrojové kolekci je nezávislé, bez sdíleného stavu zahrnutých mezi jednotlivé delegátů. Tyto operace jsou běžné v technologii LINQ to Objects a PLINQ a jsou často nazývány "*delightfully paralelní*" vzhledem k tomu, že je to možné snadno plánování z více vláken. Ale ne všechny dotazy sestávat jen z delightfully paralelních operací; ve většině případů se dotaz týká některé operátory, které buď nemůže být paralelizována nebo, který zpomalit paralelního provádění. A i s dotazy, které jsou zcela delightfully paralelní, musí i nadále oddílů zdroj dat a plánování práce na vlákna a obvykle sloučit výsledky po dokončení dotazu PLINQ. Všechny tyto operace přidání do výpočetní náklady paralelizace; Tyto náklady přidávání paralelizace se nazývají *režii*. Cílem je dosáhnout optimálního výkonu v dotazu PLINQ maximalizovat části, které jsou delightfully paralelní a části, které vyžadují režii minimalizovat. Tento článek obsahuje informace, které vám pomůže psát dotazy PLINQ, které jsou co nejúčinnější při pořád vracet správné výsledky.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Faktory, které ovlivňují výkonu dotazu PLINQ  
 V následujících částech jsou uvedeny některé z vašich nejdůležitějších faktorů této ovlivnit výkon paralelního dotazu. Toto jsou Obecné příkazy, které samy o sobě nejsou dostatečná pro předpověď výkonu dotazů ve všech případech. Jako vždy je důležité k měření skutečný výkon konkrétní dotazů na počítačích s celou řadou reprezentativní konfigurace a zatížením.  
  
1. Výpočetní náklady na celkovou práci.  
  
     K dosažení zrychlení, PLINQ dotaz musí mít dostatek delightfully paralelně prováděných úloh k vyrovnání zatížení. Práce může být vyjádřený jako výpočetní náklady na každý delegát počtem prvků zdrojové kolekce. Za předpokladu, že operace může být paralelizována, tím víc výpočetně náročné je, větší příležitosti pro zrychlení. Například pokud funkce přijímá jeden milisekund ke spuštění, sekvenční dotazu víc než 1000 prvky bude trvat jedné sekundy k provedení této operace, zatímco paralelní dotazy na počítači s čtyři jádra může trvat pouze 250 milisekund. Jde dosáhnout zrychlení 750 milisekund. V případě potřeby jedné sekundy provést pro každý prvek funkci zrychlení by 750 sekund. Pokud delegát je velmi náročná, PLINQ může nabízet výrazné zrychlení s pouze několika položkami ve zdrojové kolekci. Naopak malé zdrojové kolekce s triviální delegáty nejsou obecně vhodnými kandidáty pro PLINQ.  
  
     V následujícím příkladu je queryA pravděpodobně vhodným kandidátem pro PLINQ, za předpokladu, Select funkce zahrnuje spoustu práce. queryB není zřejmě vhodným kandidátem protože není k dispozici dostatek práce v příkazu Select a režie paralelního zpracování bude posun většinu nebo všechny zrychlení.  
  
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
  
     Tento bod je zřejmé důsledkem v předchozí části, dotazy, které jsou delightfully paralelní rychleji na počítačích s více jádry vzhledem k tomu je možné rozdělit práci mezi více souběžných vláken. Celkové množství zrychlení závisí na to, jaké je procento celkové pracovní dotazu je paralelizovat. Ale Nepředpokládejte, že všechny dotazy se spustí dvakrát jako rychle v počítači osm jader jako počítače čtyři jádra. Při ladění dotazů pro zajištění optimálního výkonu, je důležité k měření skutečné výsledky na počítačích s různým počtem jader. Tento bod má vztah k bodu #1: větších datových sad je potřeba využívat větší výpočetní prostředky.  
  
3. Počet a druh operace.  
  
     PLINQ poskytuje metodu AsOrdered operátor pro situace, ve kterých je nezbytné zachovat pořadí prvků ve zdrojové sekvenci. Náklady spojené s řazení, ale tyto náklady jsou obvykle středně velká. Funkce GroupBy a připojení k operations, stejně tak vznikne režijní náklady. PLINQ poskytuje nejlepší výkon, pokud je povoleno zpracování prvků ve zdrojové kolekci v libovolném pořadí a předat je další operátoru, jakmile jsou připravené. Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4. Formulář provádění dotazu.  
  
     Pokud ukládáte výsledků dotazu pomocí volání ToArray nebo ToList, výsledky ze všech paralelních vláken musí být sloučeny do jednoho datového struktury. To zahrnuje nevyhnutelné výpočetní náklady. Podobně pokud iterovat výsledky pomocí smyčku foreach (pro každý v jazyce Visual Basic), výsledky z pracovních vláken muset být serializován do vlákna enumerátor. Ale pokud chcete provést některé akce na základě výsledku z každé vlákno, můžete použít metodu ForAll provést tuto práci z více vláken.  
  
5. Typ možnosti sloučení.  
  
     PLINQ můžete nakonfigurovat buď uložit svůj výstup do vyrovnávací paměti a vytvořený na základě jeho v blocích nebo celou najednou celou sadu výsledků je vytvořen, nebo do datového proudu jednotlivé výsledky protože se vytvářejí. Předchozí výsledek je snížit celkový čas spuštění a druhé výsledky v nižší latence mezi elementy poskytuje.  Zatímco možnosti sloučení nemají vždy významný vliv na celkový výkon dotazů, můžou mít vliv na dosahovaný výkon protože řídí dobu uživatele musíte počkat, chcete-li zobrazit výsledky. Další informace najdete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6. Druh dělení.  
  
     V některých případech může způsobit PLINQ dotaz nad indexovanou zdrojové kolekce nevyváženou pracovní zátěže. V takovém případě je možné ke zvýšení výkonu dotazů tím, že vytvoříte vlastní dělicí metody. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Když vybere PLINQ sekvenčního režimu  
 PLINQ se vždy pokusí o provedení dotazu alespoň tak rychle, jak dotaz by spouští sekvenčně. I když PLINQ není podívejte se na tom výpočetně náročná uživatele Delegáti jsou, nebo jak velké je vstupní zdroj, vyhledejte určité dotazu "obrazce." Konkrétně hledá operátorů dotazu nebo kombinace operátorů, které obvykle způsobí dotaz, který pomaleji provést v paralelní režimu. Pokud se najde tyto tvary, PLINQ ve výchozím nastavení přejde zpět do sekvenčního režimu.  
  
 Ale po měření výkonu konkrétní dotaz, může určit, že ve skutečnosti běží rychleji v paralelní režimu. V takových případech můžete použít <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> příznak prostřednictvím <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda k vynucení PLINQ paralelizovat dotaz. Další informace najdete v tématu [jak: Určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 Následující seznam popisuje tvary dotazu PLINQ ve výchozím nastavení bude vykonán v sekvenčním režim:  
  
-   Dotazy, které obsahují s výběrem indexovat, kde indexované operátor SelectMany nebo klauzuli ElementAt po řazení nebo filtrování operátor, který se má odebrat nebo změnit jejich uspořádání původní indexy.  
  
-   Dotazy, které obsahují Take, TakeWhile –, přeskočit, SkipWhile – operátor a kde indexů ve zdrojové sekvence nejsou ve stejném pořadí.  
  
-   Dotazy, které obsahují Zip nebo SequenceEquals, pokud jeden ze zdrojů dat má původně seřazený index a jiný zdroj dat je indexované (například pole nebo IList(T)).  
  
-   Dotazy, které obsahují Concat, pokud se použije ke zdrojům dat indexovatelné.  
  
-   Dotazy, které obsahují obrátit, pokud není použita ke zdroji dat indexovatelné.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

---
title: Standardní operátory dotazu v dotazech LINQ to Entities
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 302fa281767fc95e9a9a2192382034b3a519cd92
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884866"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardní operátory dotazu v dotazech LINQ to Entities
V dotazu zadejte informace, které chcete načíst ze zdroje dat. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupeny a tvarovány dříve, než se vrátí. LINQ poskytuje sadu metod standardního dotazu, které můžete použít v dotazu. Většina z těchto metod pracovat v pořadí; v tomto kontextu, sekvence je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Funkce standardních dotazovacích operátorů dotazu obsahuje filtrování, projekce, agregace, řazení, seskupení, stránkování a další. Některé z více často používaných standardních dotazovacích operátorů mít vyhrazené klíčové slovo syntaxe tak, aby bylo možné volat pomocí syntaxe výrazu dotazu. Výraz dotazu je lépe čitelný, jiný způsob, jak vyjádřit dotaz než ekvivalentní založených na volání metody. Klauzule dotazového výrazu jsou přeloženy do volání metody dotazu v době kompilace. Seznam standardních operátorů dotazu, které mají klauzule výrazu dotazu ekvivalentní najdete v tématu [přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Operátory standardního dotazu nejsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy. Další informace najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Toto téma obsahuje informace o standardních operátorů pro dotazování, které jsou specifické pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Další informace o známých problémech v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, naleznete v tématu [známé problémy a aspekty u LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Projekce a filtrování metody  
 *Projekce* odkazuje na transformaci prvků do požadované podoby sady výsledků. Například můžete promítnout podmnožinu vlastností je třeba z každého objektu ve výsledku nastavit, můžete vlastnosti projektu a provádění matematických výpočtů na něj nebo můžete promítnout celý objekt ze sady výsledků. Projekce metody jsou `Select` a `SelectMany`.  
  
 *Filtrování* odkazuje na operaci omezení sady výsledků do obsahovat pouze prvky, které odpovídají zadané podmínce. Metody filtrování je `Where`.  
  
 Většina přetížení metod filtrování a promítání jsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], s výjimkou těch, které přijímají poziční argument.  
  
## <a name="join-methods"></a>Připojte se k metody  
 Připojení je důležité operace v dotazech, které se zaměřují zdrojů dat, které nemají žádné lze procházet vztahy mezi sebou. Spojení dvou datových zdrojů je přidružení objektů v jednom zdroji dat s objekty v jiném zdroji dat, které sdílejí společný atribut nebo vlastnost. Metody spojení jsou `Join` a `GroupJoin`.  
  
 Většina přetížení metod spojení jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Je to proto, že do zdroje dat nelze přeložit porovnávání.  
  
## <a name="set-methods"></a>Metody Set  
 Množinové operace LINQ jsou operace dotazů, které založit jejich sad výsledků dotazu na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejného nebo v jiné kolekci (nebo set). Metody set jsou `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, a `Union`.  
  
 Většina přetížení metody set jsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], i když existují určité rozdíly v chování ve srovnání s LINQ to Objects. Ale nastavené metody, které používají <xref:System.Collections.Generic.IEqualityComparer%601> nepodporuje, protože ke zdroji dat nelze přeložit porovnávání.  
  
## <a name="ordering-methods"></a>Metody řazení  
 Řazení a řazení, odkazuje na řazení elementů je sada výsledků dotazu na základě jednoho nebo více atributů. Zadáním více než jedno kritérium řazení je možné zrušit vazby v rámci skupiny.  
  
 Většina přetížení metody řazení jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IComparer%601>. Je to proto, že do zdroje dat nelze přeložit porovnávání. Pořadí metody jsou `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, a `Reverse`.  
  
 Protože spuštění dotazu na zdroji dat, pořadí chování se může lišit od dotazy spouštěné v modulu CLR. Je to proto, že možnosti, jako je například případ, řazení, kanji řazení, řazení a null řazení, lze nastavit ve zdroji dat. V závislosti na zdroji dat může tyto pořadí možnosti vytvářet různé výsledky než v modulu CLR.  
  
 Pokud zadáte stejný selektor klíče ve více než jednu operaci řazení, duplicitní řazení se nevytvoří. Toto není platný a bude vyvolána výjimka.  
  
## <a name="grouping-methods"></a>Seskupení metody  
 Seskupení odkazuje na umístění dat do skupin, aby elementy v každé skupině sdílet společný atribut. Metoda seskupení je `GroupBy`.  
  
 Většina přetížení metod seskupení jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Je to proto, že do zdroje dat nelze přeložit porovnávání.  
  
 Metody seskupení jsou namapovány na zdroji dat pomocí různých poddotazu pro selektoru klíče. Spuštění dotazu dílčí porovnání selektoru klíče pomocí sémantiky zdroje dat, včetně problémů souvisejících s porovnáním `null` hodnoty.  
  
## <a name="aggregate-methods"></a>Agregační metody  
 Operace agregace vypočítá jedinou hodnotu z kolekce hodnot. Výpočet denní teplota z za měsíc každý den teplotní hodnoty je například agregační operace. Agregační metody jsou `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum`.  
  
 Většina přetížení agregační metody jsou podporovány. Pro chování související s hodnotami null použijte metody agregační sémantiku zdroje dat. Chování metody agregace, pokud jsou zahrnuty hodnoty null se může lišit v závislosti na tom, jaké back endovému zdroji dat se používá. Metoda Aggregate chování pomocí sémantiky zdroj dat může být také liší od očekávané z metod modulu CLR. Například výchozí chování `Sum` metodou v systému SQL Server je ignorovat všechny hodnoty null namísto vyvolání výjimky.  
  
 Jakékoli výjimky, které jsou výsledkem agregace, jako je například přetečení z `Sum` fungovat, je vyvolána jako výjimky pro zdroj dat nebo Entity Framework během materializace výsledky dotazu.  
  
 Pro tyto metody, které zahrnují výpočet v sekvenci, jako například `Sum` nebo `Average`, skutečné výpočet se provádí na serveru. V důsledku toho převody typů a na serveru může dojít ke ztrátě přesnosti a výsledky mohou lišit od očekávání pomocí sémantiky CLR.  
  
 Výchozí chování metody agregace hodnot null a nenulovou je uvedeno v následující tabulce:  
  
|Metoda|Žádná data|Všechny hodnoty null|Některé hodnoty null|Žádné hodnoty null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí průměr nenulové hodnoty v pořadí.|Vypočítá průměr posloupnost číselné hodnoty.|  
|`Count`|Vrátí hodnotu 0|Vrátí počet hodnot null v sekvenci.|Vrátí hodnotu null a nenulovou hodnoty v pořadí.|Vrátí počet prvků v sekvenci.|  
|`Max`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí maximální hodnotu než null v sekvenci.|Vrátí maximální hodnotu v pořadí.|  
|`Min`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí minimální hodnotu než null v sekvenci.|Vrátí minimální hodnotu v pořadí.|  
|`Sum`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí součet nenulové hodnoty v pořadí.|Vypočítá součet prvků posloupnost číselné hodnoty.|  
  
## <a name="type-methods"></a>Typ metody  
 Dvě metody LINQ, které se zabývají převodu typu a testování jsou podporované v kontextu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. To znamená, že jediné podporované typy jsou typy, které se mapují na odpovídající [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] typu. Seznam těchto typů najdete v tématu [koncepční Model typy (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4). Typ metody jsou `Convert` a `OfType`.  
  
 `OfType` platí pro typy entit. `Convert` platí pro primitivní typy konceptuálních modelů.  C# `is` a `as` metody jsou také podporovány.  
  
## <a name="paging-methods"></a>Stránkovací metody  
 Stránkovací operace vrátí jeden element nebo více prvků ze sekvence. Jsou podporované metody stránkování `First`, `FirstOrDefault`, `Single`, `SingleOrDefault`, `Skip`, a `Take`.  
  
 Kvůli buď neschopnost mapování funkce ke zdroji dat nebo chybějící implicitní řazení sad na zdroj dat nejsou podporovány několik metod stránkování. Metody, které vrací výchozí hodnota jsou omezeny na primitivní typy konceptuálních modelů a typy odkazů s výchozí hodnotou null. Stránkovací metody, které jsou spouštěny na prázdnou sekvencí vrátí hodnotu null.  
  
## <a name="see-also"></a>Viz také  
 [Podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

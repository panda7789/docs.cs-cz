---
title: "Standardní operátory dotazu v technologii LINQ to Entities dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 94a024081acfcf4b1926f485c6dbfc2f394b418c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardní operátory dotazu v technologii LINQ to Entities dotazy
V dotazu zadejte informace, které chcete načíst z datového zdroje. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupené a ve tvaru před vrácením. LINQ poskytuje sadu metod standardní dotazu, které můžete použít v dotazu. Většina z nich pracovat pořadí; v tomto kontextu posloupnost je objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. Funkci dotazu standardní operátory dotazu obsahuje filtrování, projekce, agregace, řazení, seskupení, stránkování a další. Některé Čím více často používají standardní dotazu, operátory mít vyhrazený syntaxe – klíčové slovo, tak, aby bylo možné volat pomocí syntaxe výrazu dotazu. Výraz dotazu je jiné, srozumitelnější způsoby, jak vyjádřit dotaz než ekvivalentní na základě metod. Klauzule výraz dotazu jsou převedeny do volání metody dotazů v době kompilace. Seznam standardních operátorů dotazu s klauzulí výraz ekvivalentní dotazu najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Standardních operátorů dotazu nejsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy. Další informace najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Toto téma obsahuje informace o standardní operátory dotazu, které jsou specifické pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Další informace o známých problémech v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, najdete v části [známé problémy a důležité informace v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Projekce a filtrování metody  
 *Projekce* odkazuje na transformace prvků do formuláře požadované sadě výsledků dotazu. Například můžete promítnout podmnožinu vlastností je třeba z každého objektu ve výsledku nastavit, můžete projektu vlastnosti a na něm provádět matematický výpočet nebo můžete promítnout celý objekt ze sady výsledků. Projekce metody `Select` a `SelectMany`.  
  
 *Filtrování* odkazuje na operaci omezit tak, aby obsahovala pouze prvky, které splňují zadanou podmínku sadu výsledků dotazu. Filtrování metoda je `Where`.  
  
 Většina přetížení projekce a filtrování metody jsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], s výjimkou těch, které přijímají poziční argument.  
  
## <a name="join-methods"></a>Připojení k metody  
 Připojení je důležité operace v dotazech, které cílí zdrojů dat, které nemají žádné navigaci relace navzájem. Spojení dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty v jiných zdroj dat, které sdílejí společný atribut nebo vlastnost. Připojení k metody `Join` a `GroupJoin`.  
  
 Většina přetížení metod spojení jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Je to proto, že ke zdroji dat nejde přeložit porovnávače.  
  
## <a name="set-methods"></a>Metody Set  
 Množinové operace v technologii LINQ jsou operace dotazů, které základní jejich sad výsledků dotazu na přítomnosti nebo absenci ekvivalentní elementů v rámci stejné nebo jiné kolekce (nebo sady). Metody set `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, a `Union`.  
  
 Většina přetížení metod nastavení jsou podporovány v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], i když existují určité rozdíly v chování ve srovnání s LINQ na objekty. Ale nastavit metody, které používají <xref:System.Collections.Generic.IEqualityComparer%601> nejsou podporované, protože ke zdroji dat nejde přeložit porovnávače.  
  
## <a name="ordering-methods"></a>Řazení metody  
 Objednávání nebo řazení, odkazuje na pořadí prvků je sada výsledků dotazu na základě jednoho nebo více atributů. Zadáním více než jedno kritérium řazení, může dojít k narušení ties v rámci skupiny.  
  
 Většina přetížení řazení metod jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IComparer%601>. Je to proto, že ke zdroji dat nejde přeložit porovnávače. Řazení metody `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, a `Reverse`.  
  
 Protože dotaz proveden ve zdroji dat, řazení chování může lišit od dotazy spouštěné v modulu CLR. Je to proto, že řazení možnosti, jako je například případ uspořádání, řazení, kanji a řazení hodnotu null, lze nastavit v datovém zdroji. V závislosti na zdroji dat tyto možnosti řazení může mít různé výsledky než v modulu CLR.  
  
 Pokud zadáte stejný selektor klíče v rámci více než jedné operace řazení, duplicitní řazení vytvořil. To je neplatné a k výjimce.  
  
## <a name="grouping-methods"></a>Seskupení metody  
 Seskupení odkazuje na umístění dat do skupin tak, aby elementy v každé skupině sdílejí společný atribut. Metoda seskupení je `GroupBy`.  
  
 Většina přetížení metod seskupení jsou podporovány, s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Je to proto, že ke zdroji dat nejde přeložit porovnávače.  
  
 Seskupení metody jsou namapované na zdroji dat pomocí různých poddotazu pro selektoru klíče. Selektoru klíče porovnání poddotazu se spustí pomocí sémantiky zdroji dat, včetně problémy související s porovnávání `null` hodnoty.  
  
## <a name="aggregate-methods"></a>Agregační metody  
 Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Výpočet průměrné denní teploty z měsíc za každý den hodnoty z teploty je například operace agregace. Agregační metody `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum`.  
  
 Většina přetížení agregační metod jsou podporovány. Chování související s hodnotami null použijte metodu agregační sémantiky zdroje dat. Chování metod agregace, pokud jsou zahrnuty hodnoty null se může lišit v závislosti na zdroj dat back-end, který je používán. Metoda Aggregate chování pomocí sémantiky zdroje dat, může být také liší od očekávané z metod modulu CLR. Například výchozí chování `Sum` metoda na serveru SQL Server bude ignorovat všechny hodnoty null místo došlo k výjimce.  
  
 Jakékoli výjimky, které jsou výsledkem agregace, jako je přetečení z `Sum` fungovat, je vyvolána jako výjimky pro zdroj dat nebo Entity Framework během materialization výsledků dotazu.  
  
 Pro tyto metody, které zahrnují výpočtu přes sekvenci, jako například `Sum` nebo `Average`, skutečný výpočet se provádí na serveru. V důsledku toho převody typu a na serveru může dojít ke ztrátě přesnosti a výsledky se může lišit od očekávané pomocí sémantiky CLR.  
  
 V následující tabulce je zobrazena výchozí chování agregační metody pro hodnotu null nebo nenulových hodnot:  
  
|Metoda|Žádná data|Všechny hodnoty null|Některé hodnoty null|Žádné hodnoty null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí průměr neprázdných hodnot v pořadí.|Vypočítá průměrnou hodnotu posloupnost číselné hodnoty.|  
|`Count`|Vrátí hodnotu 0|Vrátí počet hodnoty null v pořadí.|Vrátí počet hodnot null a nesmí být nulová v pořadí.|Vrátí počet prvků v pořadí.|  
|`Max`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí maximální hodnotu než null v pořadí.|Vrací maximální hodnotu v pořadí.|  
|`Min`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí minimální hodnotu než null v pořadí.|Vrátí minimální hodnotu v pořadí.|  
|`Sum`|Vrátí hodnotu null.|Vrátí hodnotu null.|Vrátí součet hodnotu než null v pořadí.|Vypočítá součet posloupnosti číselné hodnoty.|  
  
## <a name="type-methods"></a>Typ metody  
 Tyto dvě metody LINQ, které pracují s převod typů a testování jsou podporované v kontextu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. To znamená, že se pouze na podporované typy, které mapují na odpovídající [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] typu. Seznam těchto typů najdete v tématu [konceptuálního modelu typy (CSDL)](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4). Typ metody `Convert` a `OfType`.  
  
 `OfType`je podporován pro typy entit. `Convert`je podporován pro koncepční model primitivní typy.  C# `is` a `as` metody jsou také podporovány.  
  
## <a name="paging-methods"></a>Metody stránkování  
 Stránkovací operace vrácení jedné, konkrétní element z sekvenci. Element metody `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take`, `TakeWhile`.  
  
 Několik metod stránkování nejsou podporovány v důsledku neschopnost mapování funkce ke zdroji dat nebo chybějícím implicitní řazení sad na datovém zdroji. Metody, které vracejí výchozí hodnota jsou omezeny na konceptuální model primitivní typy a typy odkazu s hodnotou null výchozí hodnoty. Stránkování metody, které jsou spouštěny na prázdnou sekvencí vrátí hodnotu null.  
  
## <a name="see-also"></a>Viz také  
 [Podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Přehled standardních operátorů dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

---
title: Standardní operátory dotazů LINQ to Entities
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 76d32db5c81d88db28194da19e722b1a80c1a870
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249151"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardní operátory dotazů LINQ to Entities
V dotazu zadáte informace, které chcete načíst ze zdroje dat. Dotaz může také určit, jak se mají tyto informace seřadit, seskupit a tvarovat před tím, než se vrátí. LINQ poskytuje sadu standardních metod dotazů, které můžete použít v dotazu. Většina těchto metod pracuje na sekvencích. v tomto kontextu je sekvence objekt, jehož typ implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní <xref:System.Linq.IQueryable%601> nebo rozhraní. Standardní funkce dotazů operátorů dotazu zahrnuje filtrování, projekci, agregace, řazení, seskupování, stránkování a další. Některé z často používaných standardních operátorů dotazů mají vyhrazenou syntaxi klíčového slova, aby je bylo možné volat pomocí syntaxe výrazu dotazu. Výraz dotazu je jiný, čitelnější způsob, jak vyjádřit dotaz než ekvivalent založený na metodě. Klauzule dotazového výrazu jsou přeloženy do volání metod dotazů v době kompilace. Seznam standardních operátorů dotazu, které mají ekvivalentní klauzule výrazů dotazu, najdete v tématu [Přehled standardních operátorů dotazů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 V LINQ to Entitiesch dotazech nejsou podporovány všechny standardní operátory dotazu. Další informace najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md). Toto téma poskytuje informace o standardních operátorech dotazu, které jsou specifické pro LINQ to Entities. Další informace o známých problémech v LINQ to Entitiesch dotazech najdete v tématu [známé problémy a důležité informace v LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Metody projekce a filtrování  
 *Projekce* odkazuje na transformaci prvků sady výsledků dotazu do požadovaného formuláře. Například můžete promítnout určitou podmnožinu vlastností, které potřebujete z každého objektu v sadě výsledků dotazu, můžete projektovat vlastnost a provést na ní matematický výpočet nebo můžete celý objekt promítnout ze sady výsledků dotazu. Metody projekce jsou `Select` a `SelectMany`.  
  
 *Filtrování* odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce. Metoda filtrování je `Where`.  
  
 Většina přetížení metod projekce a filtrování je v LINQ to Entities podporována s výjimkou těch, které přijímají poziční argument.  
  
## <a name="join-methods"></a>Metody join  
 Spojování je důležitá operace v dotazech, které cílí na zdroje dat, které nemají vzájemně naviguje vztahy. Spojení dvou zdrojů dat je přidružení objektů v jednom zdroji dat k objektům v jiném zdroji dat, které sdílejí společný atribut nebo vlastnost. Metody join jsou `Join` a `GroupJoin`.  
  
 Většina přetížení metod JOIN je podporována s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Důvodem je, že porovnávací nástroj nelze přeložit na zdroj dat.  
  
## <a name="set-methods"></a>Metody set  
 Operace Set v LINQ jsou operace dotazů, které jsou základem jejich sad výsledků, nebo nepřítomnost ekvivalentních prvků v rámci stejné nebo jiné kolekce (nebo sady). Metody set `All`jsou, `Any`, `Concat` ,`DefaultIfEmpty`,, ,`EqualAll`,, a.`Intersect` `Except` `Distinct` `Contains` `Union`  
  
 Většina přetížení metod set je v LINQ to Entities podporovaná, i když jsou v porovnání s LINQ to Objectsy rozdíly v chování. Nicméně metody, které používají výjimku <xref:System.Collections.Generic.IEqualityComparer%601> , nejsou podporovány, protože porovnávání nelze přeložit na zdroj dat.  
  
## <a name="ordering-methods"></a>Metody řazení  
 Řazení nebo řazení odkazuje na řazení prvků sady výsledků na základě jednoho nebo více atributů. Zadáním více než jednoho kritéria řazení můžete rušit vazby v rámci skupiny.  
  
 Většina přetížení metod řazení je podporována s výjimkou těch, které používají <xref:System.Collections.Generic.IComparer%601>. Důvodem je, že porovnávací nástroj nelze přeložit na zdroj dat. Metody `OrderBy`řazení jsou, `ThenBy`, `OrderByDescending` ,`ThenByDescending`a .`Reverse`  
  
 Vzhledem k tomu, že je dotaz spuštěn ve zdroji dat, chování pořadí se může lišit od dotazů provedených v modulu CLR. Důvodem je, že možnosti řazení, například řazení případů, řazení kanji a řazení hodnoty null, lze nastavit ve zdroji dat. V závislosti na zdroji dat můžou tyto možnosti řazení vést k různým výsledkům než v modulu CLR.  
  
 Pokud zadáte stejný selektor klíče ve více než jedné operaci řazení, bude vytvořeno duplicitní řazení. Toto není platné a vyvolá se výjimka.  
  
## <a name="grouping-methods"></a>Metody seskupení  
 Seskupení odkazuje na umístění dat do skupin, aby elementy v každé skupině sdílely společný atribut. Metoda seskupení je `GroupBy`.  
  
 Většina přetížení metod seskupení je podporována s výjimkou těch, které používají <xref:System.Collections.Generic.IEqualityComparer%601>. Důvodem je, že porovnávací nástroj nelze přeložit na zdroj dat.  
  
 Metody seskupení jsou mapovány na zdroj dat pomocí samostatného dílčího dotazu pro selektor klíčů. Porovnání výběru klíčů dílčí dotaz je spuštěn pomocí sémantiky zdroje dat, včetně problémů souvisejících s porovnáváním `null` hodnot.  
  
## <a name="aggregate-methods"></a>Agregační metody  
 Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Například výpočet průměrné denní teploty z hodnoty denních teplot v měsíci je operace agregace. `Aggregate`Agregační metody jsou, `Average`, `Count`,,, a .`Sum` `LongCount` `Max` `Min`  
  
 Většina přetížení agregačních metod je podporována. Pro chování související s hodnotami null využívají agregační metody sémantiku zdroje dat. Chování metod agregace při použití hodnot null může být odlišné v závislosti na použitém zdroji dat back-end. Chování agregační metody pomocí sémantiky zdroje dat se může také lišit od toho, co se očekává od metod CLR. Například výchozí chování pro `Sum` metodu na SQL Server je ignorovat hodnoty null namísto vyvolání výjimky.  
  
 Všechny výjimky, které jsou výsledkem agregace, například přetečení z `Sum` funkce, jsou vyvolány jako výjimky zdroje dat nebo Entity Framework výjimky během materializace výsledků dotazu.  
  
 Pro ty metody, které zahrnují výpočet přes sekvenci, jako `Sum` je nebo `Average`, se na serveru provádí skutečný výpočet. V důsledku toho může dojít k převodům typu a ztrátě přesnosti na serveru a výsledky se mohou lišit od toho, co se očekává pomocí sémantiky CLR.  
  
 Výchozí chování agregačních metod pro hodnoty null/non-null je uvedeno v následující tabulce:  
  
|Metoda|Žádná data|Všechny hodnoty null|Některé hodnoty null|Žádné hodnoty null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Vrací hodnotu null.|Vrací hodnotu null.|Vrátí průměr hodnot, které nejsou null v sekvenci.|Vypočítá průměr posloupnosti číselných hodnot.|  
|`Count`|Vrátí 0|Vrátí počet hodnot null v sekvenci.|Vrátí počet hodnot null a jiných než null v sekvenci.|Vrátí počet prvků v sekvenci.|  
|`Max`|Vrací hodnotu null.|Vrací hodnotu null.|Vrátí maximální hodnotu, která není null v sekvenci.|Vrátí maximální hodnotu v sekvenci.|  
|`Min`|Vrací hodnotu null.|Vrací hodnotu null.|Vrátí minimální hodnotu, která není null v sekvenci.|Vrátí minimální hodnotu v sekvenci.|  
|`Sum`|Vrací hodnotu null.|Vrací hodnotu null.|Vrátí součet hodnoty, která není null v sekvenci.|Vypočítá součet posloupnosti číselných hodnot.|  
  
## <a name="type-methods"></a>Metody typu  
 Dvě metody LINQ, které se týkají konverze a testování typu, jsou podporovány v kontextu Entity Framework. To znamená, že jedinými podporovanými typy jsou typy, které se mapují na příslušný typ Entity Framework. Seznam těchto typů naleznete v tématu [typy konceptuálních modelů (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl). Metody typu jsou `Convert` a `OfType`.  
  
 `OfType`je podporováno pro typy entit. `Convert`je podporováno pro primitivní typy konceptuálního modelu.  Podporovány jsou `as` i metody a.`is` C#  
  
## <a name="paging-methods"></a>Metody stránkování  
 Operace stránkování vrací jeden prvek nebo více prvků z sekvence. Podporované metody stránkování jsou `First`, `FirstOrDefault`, `Single` `SingleOrDefault`,, `Skip`a. `Take`  
  
 Počet metod stránkování není podporován, protože buď není možné mapovat funkce na zdroj dat, nebo na chybějící implicitní řazení sad ve zdroji dat. Metody, které vracejí výchozí hodnotu, jsou omezeny na primitivní typy konceptuálního modelu a odkazují na typy s nulovým výchozím nastavením. Metody stránkování, které jsou spouštěny v prázdné sekvenci, vrátí hodnotu null.  
  
## <a name="see-also"></a>Viz také:

- [Podporované a nepodporované metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)
- [Přehled standardních operátorů dotazu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))

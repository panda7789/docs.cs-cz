---
title: 'Průvodce: Zápis dotazů v jazyce C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: ffff8317e6524acc877b7d0851e5a1b37967b1f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154073"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Průvodce: Zápis dotazů v jazyce C# (LINQ)
Tento návod ukazuje funkce jazyka C#, které se používá k zápisu LINQ – výrazy dotazů.  
  
## <a name="create-a-c-project"></a>Vytvoření projektu v jazyce C#  
  
> [!NOTE]
>  Následující pokyny jsou určené pro Visual Studio. Pokud používáte různé vývojové prostředí, vytvořte projekt konzoly s odkazem na knihovnu System.Core.dll a `using` směrnice pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Vytvoření projektu v sadě Visual Studio  
  
1.  Spusťte Visual Studio.  
  
2.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  Rozbalte **nainstalováno**, rozbalte **šablony**, rozbalte **Visual C#** a klikněte na tlačítko **konzolovou aplikaci**.  
  
4.  V **název** textového pole zadejte jiný název nebo přijměte výchozí název a klikněte na tlačítko **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníka řešení**.  
  
5.  Všimněte si, že váš projekt obsahuje odkaz na System.Core.dll a `using` směrnice pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
## <a name="create-an-in-memory-data-source"></a>Vytvoření zdroje dat v paměti  
 Zdroj dat pro dotazy je jednoduchý seznam `Student` objekty. Každý `Student` záznam obsahuje jméno, příjmení a pole celých čísel, která představuje jejich výsledky testu ve třídě. Zkopírujte tento kód do vašeho projektu. Mějte na paměti následující vlastnosti:  
  
-   `Student` Třídy se skládá z automaticky implementované vlastnosti.  
  
-   Každý student v seznamu je inicializovat pomocí inicializátoru objektu.  
  
-   Samotný seznam je inicializovat pomocí inicializátoru kolekce.  
  
 Tato struktura celé datové bude inicializována a bez explicitní volání konstruktoru nebo přístup ke členu explicitní vytvoření instance. Další informace o těchto nových funkcích najdete v tématu [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
-   Přidat `Student` třídy a inicializovaný seznam studenty, aby `Program` třídu ve vašem projektu.  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového objektu Student do seznamu Students  
  
1.  Přidat nový `Student` k `Students` seznamu a pomocí názvu a otestovat skóre, které se podle vašeho výběru. Zadejte všechny nové studentské informace, abychom tak získali lepší Seznamte se se syntaxí pro inicializátoru objektu.  
  
## <a name="create-the-query"></a>Vytvoření dotazu  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
-   V aplikaci prvku `Main` metody vytvoření jednoduchého dotazu, který, pokud je spuštěn, bude vytvoření seznamu Všichni studenti, jehož skóre na první test byl větší než 90. Upozorňujeme, že celý `Student` vybrán objekt, je typ dotazu `IEnumerable<Student>`. I když kód může také použití implicitního zápisu pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo, explicitní zadání slouží k jasně ukazuje výsledky. (Další informace o `var`, naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Všimněte si také, že v dotazu proměnná rozsahu `student`, slouží jako odkaz na každé `Student` ve zdroji, poskytují přístup ke členu pro každý objekt.  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Provedení dotazu  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1.  Teď zapisovat `foreach` smyčku, která způsobí, že ke spuštění dotazu. Mějte na paměti následující skutečnosti související kód:  
  
    -   Každý prvek ve vrácené posloupnosti je přístupné prostřednictvím proměnné iterace ve `foreach` smyčky.  
  
    -   Typ této proměnné je `Student`, a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>`.  
  
2.  Po přidání tohoto kódu sestavte a spusťte aplikaci a ověřte výsledky v **konzoly** okna.  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Přidání další podmínky filtru  
  
1.  Můžete zkombinovat více logických podmínek v `where` klauzuli pro další upřesnění dotazu. Následující kód přidává podmínku tak, že dotaz vrací ty studenty, jehož první skóre bylo víc než 90 a jejichž poslední skóre nižší než 80. `where` Klauzule by měla vypadat podobně jako následující kód.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Úprava dotazu  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1.  Ji bude snazší výsledky kontroly, pokud se nějaký druh pořadí. Můžete si objednat vrácená sekvence podle jakékoli přístupné pole ve zdrojové elementy. Například následující `orderby` klauzule řadí výsledky v abecedním pořadí od A až Z podle poslední název každého studenta. Přidejte následující `orderby` klauzule dotazu, hned po `where` příkazu a před `select` – příkaz:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2.  Teď změňte `orderby` klauzule tak, že v obráceném pořadí řadí výsledky podle skóre v prvním testu z nejvyšším skóre skóre.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3.  Změnit `WriteLine` řetězec formátu, kde lze zobrazit skóre:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Seskupení výsledků  
  
1.  Seskupení je výkonná funkce ve výrazech dotazů. Dotazy s klauzulí skupiny vytvoří posloupnost skupin a obsahuje samotnou skupinu `Key` a sekvenci, která se skládá ze všech členů této skupiny. Následující nový dotaz seskupí studenty s použitím první písmeno jeho příjmení jako klíč.  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Všimněte si, že je typ dotazu se změnilo. Nyní generuje sekvenci skupiny, které mají `char` typ jako klíč a sekvencí `Student` objekty. Protože došlo ke změně typu dotazu, následující změny kódu `foreach` provádění smyčky také:  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Spusťte aplikaci a zobrazit výsledky v **konzoly** okna.  
  
     Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Převedení proměnných na implicitně typované proměnné  
  
1.  Explicitně kódování `IEnumerables` z `IGroupings` může být zdlouhavé. Můžete napsat stejný dotaz a `foreach` smyčky mnohem snadněji pomocí `var`. `var` – Klíčové slovo nezmění typy objektů; právě instruuje kompilátor k odvození typů. Změna typu `studentQuery` a iterační proměnné `group` k `var` a spusťte dotaz znovu. Všimněte si, že v vnitřní `foreach` smyčky, iterační proměnná je stále zadán jako `Student`, a dotaz funguje stejně jako v minulosti. Změnit `s` iterační proměnné a `var` a spusťte dotaz znovu. Uvidíte, že dostanete přesně stejné výsledky.  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Další informace o [var](../../../../csharp/language-reference/keywords/var.md), naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Seřazení skupin podle hodnoty jejich klíče  
  
1.  Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí. Chcete-li toto nastavení změnit, je nutné zadat `orderby` klauzule po `group` klauzuli. Ale pro použití `orderby` klauzule, musíte nejprve identifikátor, který slouží jako odkaz na skupinách vytvořených skriptem `group` klauzuli. Zadejte identifikátor pomocí `into` – klíčové slovo, následujícím způsobem:  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Při spuštění tohoto dotazu, zobrazí se, že tyto skupiny jsou nyní seřadit v abecedním pořadí.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Zavedení identifikátoru s použitím klíčového slova let  
  
1.  Můžete použít `let` – klíčové slovo zavedení identifikátoru pro libovolný výsledek výrazu ve výrazu dotazu. Tento identifikátor může být pro přehlednost jako v následujícím příkladu, nebo ho můžete zvýšit výkon ukládáním výsledky výrazu tak, aby nemá vypočítávat více než jednou.  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Použití syntaxe využívající metody ve výrazu dotazu  
  
1.  Jak je popsáno v [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), nějakých operací dotazů lze vyjádřit pouze pomocí syntaxe metody. Následující kód vypočítá celkové skóre pro každou `Student` ve zdrojové sekvence a poté zavolá `Average()` metodu na výsledky dotazu pro výpočet průměrné skóre třídy.
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Transformace nebo projekce v klauzuli select  
  
1.  Je velmi běžné, že dotaz, který vytvoří posloupnost, jehož prvky se liší od elementy ve zdrojových posloupností. Odstranit nebo okomentovat předchozí dotaz a provádění smyčky a nahraďte ho následujícím kódem. Všimněte si, že dotaz vrací posloupnost řetězců (není `Students`), a tuto skutečnost se projeví v `foreach` smyčky.  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Kód výše v tomto názorném postupu uvedeno, že třída průměrné skóre je přibližně 334. K vytvoření sekvence `Students` jehož celkovým skóre je větší než průměr třídy společně s jejich `Student ID`, můžete použít anonymní typ v `select` – příkaz:  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Další kroky  
 Jakmile se seznámíte s základní aspektů práce s dotazy v jazyce C#, jste připravení číst dokumentaci a ukázky pro konkrétní typ zprostředkovatele LINQ, které vás zajímají:  
  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [Technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také

- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)

---
title: 'Návod: Zápis dotazů v C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73418058"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Návod: Zápis dotazů v C# (LINQ)
Tento návod ukazuje funkce jazyka C#, které se používají k zápisu výrazů dotazu LINQ.  
  
## <a name="create-a-c-project"></a>Vytvoření projektu v jazyce C#  
  
> [!NOTE]
> Následující pokyny jsou pro Visual Studio. Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem `using` na soubor <xref:System.Linq?displayProperty=nameWithType> System.Core.dll a direktivu oboru názvů.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Vytvoření projektu v sadě Visual Studio  
  
1. Spusťte Visual Studio.  
  
2. Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.  
  
     Otevře se dialogové okno **Nový projekt.**  
  
3. Rozbalte **Nainstalované**, **rozbalte položku Šablony**, rozbalte **položku Visual C#** a pak zvolte **Konzolová aplikace**.  
  
4. Do textového pole **Název** zadejte jiný název nebo přijměte výchozí název a pak zvolte tlačítko **OK.**  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5. Všimněte si, že váš projekt má odkaz `using` na System.Core.dll a směrnice pro obor <xref:System.Linq?displayProperty=nameWithType> názvů.  
  
## <a name="create-an-in-memory-data-source"></a>Vytvoření zdroje dat v paměti  
 Zdroj dat pro dotazy je jednoduchý `Student` seznam objektů. Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, které představuje jejich výsledky testů ve třídě. Zkopírujte tento kód do projektu. Všimněte si následujících vlastností:  
  
- Třída `Student` se skládá z automaticky implementovaných vlastností.  
  
- Každý student v seznamu je inicializován inicializátorem objektu.  
  
- Samotný seznam je inicializován inicializátorem kolekce.  
  
 Celá tato datová struktura bude inicializována a vytvořena bez explicitních volání libovolného konstruktoru nebo explicitního přístupu členů. Další informace o těchto nových funkcích naleznete [v tématu Automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
- Přidejte `Student` do `Program` kurzu v projektu kurz a inicializovaný seznam studentů.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového objektu Student do seznamu Students  
  
1. Přidejte `Student` do `Students` seznamu nové a použijte název a výsledky testů podle vašeho výběru. Zkuste zadat všechny nové informace o studentovi, abyste se lépe naučili syntaxi inicializátoru objektu.  
  
## <a name="create-the-query"></a>Vytvoření dotazu  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
- V `Main` metodě aplikace vytvořte jednoduchý dotaz, který při spuštění vytvoří seznam všech studentů, jejichž skóre v prvním testu bylo větší než 90. Všimněte si, `Student` že vzhledem k tomu, `IEnumerable<Student>`že je vybrán celý objekt, je typ dotazu . Přestože kód může také použít implicitní psaní pomocí klíčového slova [var,](../../../language-reference/keywords/var.md) explicitní psaní se používá k jasnému ilustraci výsledků. (Další informace `var`o , naleznete [v tématu implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Všimněte si také, že `student`proměnná rozsahu dotazu, , slouží jako odkaz na každý `Student` ve zdroji, poskytuje přístup členů pro každý objekt.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Provedení dotazu  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1. Nyní napište `foreach` smyčku, která způsobí spuštění dotazu. Všimněte si následujícího kódu:  
  
    - Každý prvek ve vrácené posloupnosti je `foreach` přístupný prostřednictvím iterace proměnné ve smyčce.  
  
    - Typ této proměnné `Student`je a typ proměnné dotazu `IEnumerable<Student>`je kompatibilní .  
  
2. Po přidání tohoto kódu vytvořte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly.**  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Přidání další podmínky filtru  
  
1. Můžete kombinovat více booleovské `where` podmínky v klauzuli za účelem dalšího upřesnění dotazu. Následující kód přidá podmínku tak, aby dotaz vrátí ty studenty, jejichž první skóre bylo více než 90 a jehož poslední skóre bylo menší než 80. Klauzule `where` by se měla podobat následující kód.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Další informace naleznete v tématu [where clause](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Úprava dotazu  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1. Bude snazší skenovat výsledky, pokud jsou v nějakém pořadí. Vrácenou sekvenci můžete seřadit podle libovolného přístupného pole ve zdrojových prvcích. Například následující `orderby` klauzule seřazuje výsledky v abecedním pořadí od A do Z podle příjmení každého studenta. Přidejte `orderby` do dotazu následující klauzuli, hned za `where` příkaz a před `select` příkaz:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Nyní změňte `orderby` klauzuli tak, aby se výsledky seřadila v opačném pořadí podle skóre v prvním testu, od nejvyššího skóre k nejnižšímu skóre.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Změňte `WriteLine` formátovací řetězec tak, aby bylo vidět skóre:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Další informace naleznete v [tématu orderby klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Seskupení výsledků  
  
1. Seskupení je výkonná funkce ve výrazech dotazu. Dotaz s klauzulí group vytvoří posloupnost skupin a `Key` každá skupina sama obsahuje a a posloupnost, která se skládá ze všech členů této skupiny. Následující nový dotaz seskupuje studenty pomocí prvního písmene jejich příjmení jako klíče.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Všimněte si, že typ dotazu se nyní změnil. Nyní vytváří posloupnost skupin, `char` které mají typ jako klíč `Student` a posloupnost objektů. Vzhledem k tomu, že se typ `foreach` dotazu změnil, následující kód změní také smyčku spuštění:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Spusťte aplikaci a zobrazte výsledky v okně **konzoly.**  
  
     Další informace naleznete v tématu [group clause](../../../language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Převedení proměnných na implicitně typované proměnné  
  
1. Explicitně `IEnumerables` `IGroupings` kódování může rychle stát únavné. Můžete napsat stejný dotaz `foreach` a smyčky mnohem `var`pohodlněji pomocí . Klíčové `var` slovo nezmění typy objektů; pouze instruuje kompilátor odvodit typy. Změňte typ `studentQuery` a itetivní proměnnou `group` a `var` znovu spusťte dotaz. Všimněte si, `foreach` že ve vnitřní smyčce `Student`je proměnná iterace stále zadána jako a dotaz funguje stejně jako dříve. Změňte `s` proměnnou `var` iterace na a spusťte dotaz znovu. Vidíte, že dostanete přesně stejné výsledky.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Další informace o [var](../../../language-reference/keywords/var.md)naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Seřazení skupin podle hodnoty jejich klíče  
  
1. Při spuštění předchozího dotazu zjistíte, že skupiny nejsou v abecedním pořadí. Chcete-li to změnit, `orderby` musíte `group` zadat klauzuli za klauzulí. Ale chcete-li použít `orderby` klauzuli, nejprve potřebujete identifikátor, který `group` slouží jako odkaz na skupiny vytvořené klauzulí. Identifikátor zadáte pomocí klíčového `into` slova následujícím způsobem:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Při spuštění tohoto dotazu uvidíte, že skupiny jsou nyní seřazeny v abecedním pořadí.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Zavedení identifikátoru s použitím klíčového slova let  
  
1. Pomocí klíčového `let` slova můžete zavést identifikátor pro libovolný výraz, který má výraz dotazu. Tento identifikátor může být pohodlí, jako v následujícím příkladu, nebo může zvýšit výkon uložením výsledků výrazu tak, aby není nutné vypočítat vícekrát.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Další informace naleznete v tématu [let klauzule](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Použití syntaxe využívající metody ve výrazu dotazu  
  
1. Jak je popsáno v [syntaxi dotazu a syntaxi metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody. Následující kód vypočítá celkové skóre `Student` pro každý ve zdrojové `Average()` sekvenci a potom volá metodu na výsledky tohoto dotazu k výpočtu průměrné skóre třídy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Transformace nebo projekce v klauzuli select  
  
1. Je velmi běžné, že dotaz vytvořit sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích. Odstraňte nebo zakomentujte předchozí smyčku dotazu a spuštění a nahraďte ji následujícím kódem. Všimněte si, že dotaz vrátí `Students`posloupnost řetězců (ne `foreach` ) a tato skutečnost se projeví ve smyčce.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kód dříve v tomto návodu uvedeno, že průměrné skóre třídy je přibližně 334. Chcete-li vytvořit `Students` posloupnost, jejíž celkové skóre `Student ID`je větší než průměr třídy, spolu s jejich , můžete použít anonymní typ v příkazu: `select`  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Další kroky  
 Poté, co jste obeznámeni se základními aspekty práce s dotazy v jazyce C#, jste připraveni přečíst dokumentaci a ukázky pro konkrétní typ poskytovatele LINQ, který vás zajímá:  
  
 [Technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ do XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ na objekty (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také

- [Dotaz integrovaný jazykem (LINQ) (C#)](./index.md)
- [Výrazy dotazu LINQ](../../../linq/index.md)

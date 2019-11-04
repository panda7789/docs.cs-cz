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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418058"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Návod: Zápis dotazů v C# (LINQ)
Tento návod ukazuje funkce C# jazyka, které se používají k zápisu výrazů dotazů LINQ.  
  
## <a name="create-a-c-project"></a>Vytvoření projektu v jazyce C#  
  
> [!NOTE]
> Následující pokyny jsou pro Visual Studio. Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem na System. Core. dll a direktivu `using` pro obor názvů <xref:System.Linq?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Vytvoření projektu v aplikaci Visual Studio  
  
1. Spusťte Visual Studio.  
  
2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
     Otevře se dialogové okno **Nový projekt** .  
  
3. Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **vizuál C#** a pak zvolte možnost **Konzolová aplikace**.  
  
4. Do textového pole **název** zadejte jiný název nebo přijměte výchozí název a pak klikněte na tlačítko **OK** .  
  
     Nový projekt se zobrazí v **Průzkumník řešení**.  
  
5. Všimněte si, že váš projekt má odkaz na System. Core. dll a direktivu `using` pro obor názvů <xref:System.Linq?displayProperty=nameWithType>.  
  
## <a name="create-an-in-memory-data-source"></a>Vytvoření zdroje dat v paměti  
 Zdrojem dat pro dotazy je jednoduchý seznam `Student` objektů. Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, která představují jejich skóre testů ve třídě. Zkopírujte tento kód do projektu. Všimněte si následujících vlastností:  
  
- Třída `Student` se skládá z automaticky implementovaných vlastností.  
  
- Každý student v seznamu se inicializuje s inicializátorem objektu.  
  
- Samotný seznam je inicializován s inicializátorem kolekce.  
  
 Tato Celá datová struktura bude inicializována a vytvořena bez explicitního volání jakéhokoliv konstruktoru nebo explicitního přístupu ke členu. Další informace o těchto nových funkcích naleznete v tématu [automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
- Přidejte třídu `Student` a inicializovaný seznam studentů do třídy `Program` ve vašem projektu.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového objektu Student do seznamu Students  
  
1. Přidejte nový `Student` do seznamu `Students` a použijte název a hodnocení podle vašeho výběru. Zkuste zadat všechny informace o novém studentovi, aby se lépe dozvěděla syntaxe inicializátoru objektu.  
  
## <a name="create-the-query"></a>Vytvoření dotazu  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
- V metodě `Main` aplikace vytvořte jednoduchý dotaz, který při spuštění vytvoří seznam všech studentů, jejichž skóre prvního testu bylo větší než 90. Všimněte si, že vzhledem k tomu, že je vybrán celý objekt `Student`, je typ dotazu `IEnumerable<Student>`. I když kód může také použít implicitní zadání pomocí klíčového slova [var](../../../language-reference/keywords/var.md) , explicitní psaní se používá k jasné ilustraci výsledků. (Další informace o `var`naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Všimněte si také, že proměnná rozsahu dotazu `student`, slouží jako odkaz na každý `Student` ve zdroji a poskytuje pro každý objekt přístup pro členy.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Provedení dotazu  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1. Nyní zapište smyčku `foreach`, která způsobí, že se dotaz spustí. Všimněte si následujícího kódu:  
  
    - Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace ve smyčce `foreach`.  
  
    - Typ této proměnné je `Student`a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>`.  
  
2. Po přidání tohoto kódu Sestavte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly** .  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Přidání další podmínky filtru  
  
1. Můžete zkombinovat více logických podmínek v klauzuli `where`, aby bylo možné dále upřesnit dotaz. Následující kód přidá podmínku, takže dotaz vrátí takové studenty, jejichž první skóre bylo nad 90 a jejichž poslední skóre bylo menší než 80. Klauzule `where` by se měla podobat následujícímu kódu.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Úprava dotazu  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1. Vyhledávání výsledků bude snazší, pokud jsou v nějakém typu pořadí. Vrácenou sekvenci můžete seřadit podle libovolného dostupného pole ve zdrojových prvcích. Například následující klauzule `orderby` seřadí výsledky v abecedním pořadí od A do Z v závislosti na posledním názvu každého studenta. Přidejte následující klauzuli `orderby` do dotazu, hned za příkaz `where` a před příkaz `select`:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Nyní změňte klauzuli `orderby` tak, aby odpovídala výsledkům v obráceném pořadí podle skóre prvního testu, od nejvyššího skóre až po nejnižší skóre.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Změňte řetězec formátu `WriteLine`, abyste viděli skóre:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Seskupení výsledků  
  
1. Seskupení je výkonná funkce ve výrazech dotazů. Dotaz s klauzulí GROUP vytvoří posloupnost skupin a každá skupina obsahuje `Key` a sekvenci, která se skládá ze všech členů této skupiny. Následující nové dotazy seskupují studenty pomocí prvního písmene jejich příjmení jako klíče.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Všimněte si, že typ dotazu byl nyní změněn. Nyní vytváří sekvenci skupin, které mají typ `char` jako klíč, a sekvenci objektů `Student`. Vzhledem k tomu, že se typ dotazu změnil, následující kód změní také smyčku spuštění `foreach`:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Spusťte aplikaci a zobrazte výsledky v okně **konzoly** .  
  
     Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Převedení proměnných na implicitně typované proměnné  
  
1. Explicitní kódování `IEnumerables` `IGroupings` se může rychle stát zdlouhavě. Stejný dotaz a `foreach`ovou smyčku můžete napsat mnohem pohodlně pomocí `var`. Klíčové slovo `var` nemění typy vašich objektů; pouze instruuje kompilátor, aby odvodí typy. Změňte typ `studentQuery` a proměnnou iterace `group` na `var` a znovu spusťte dotaz. Všimněte si, že ve vnitřní `foreach` smyčce je proměnná iterace zapsána jako `Student`a dotaz funguje stejně jako dřív. Změňte `s` proměnnou iterace na `var` a spusťte dotaz znovu. Vidíte, že se vám přesně vrátí stejné výsledky.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Další informace o funkci [var](../../../language-reference/keywords/var.md)naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Seřazení skupin podle hodnoty jejich klíče  
  
1. Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí. Chcete-li toto změnit, je nutné zadat klauzuli `orderby` za klauzulí `group`. Chcete-li však použít klauzuli `orderby`, nejprve potřebujete identifikátor, který slouží jako odkaz na skupiny vytvořené klauzulí `group`. Identifikátor zadáte pomocí klíčového slova `into` následujícím způsobem:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Když spustíte tento dotaz, uvidíte, že se skupiny teď řadí v abecedním pořadí.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Zavedení identifikátoru s použitím klíčového slova let  
  
1. Klíčové slovo `let` lze použít k představení identifikátoru pro jakýkoli výsledek výrazu ve výrazu dotazu. Tento identifikátor může být pohodlí, jak je uvedeno v následujícím příkladu, nebo může zvýšit výkon tím, že uloží výsledky výrazu tak, aby se nemusela vypočítat víckrát.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Použití syntaxe využívající metody ve výrazu dotazu  
  
1. Jak je popsáno v syntaxi [dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody. Následující kód vypočítá celkové skóre pro každý `Student` ve zdrojové sekvenci a poté zavolá metodu `Average()` ve výsledcích tohoto dotazu pro výpočet průměrného skóre třídy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Transformace nebo projekce v klauzuli select  
  
1. Je velmi běžné, že dotaz vytvoří sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích. Odstraňte nebo zakomentujte předchozí dotaz a smyčku spuštění a nahraďte ji následujícím kódem. Všimněte si, že dotaz vrátí sekvenci řetězců (není `Students`) a tento fakt se projeví ve `foreach` smyčce.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kód uvedený výše v tomto návodu uvádí, že průměrné skóre třídy je přibližně 334. Chcete-li vytvořit sekvenci `Students`, jejichž celkové skóre je větší než průměr třídy, spolu s jejich `Student ID`, můžete v příkazu `select` použít anonymní typ:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Další kroky  
 Jakmile se seznámíte se základními aspekty práce s dotazy v C#nástroji, můžete si přečíst dokumentaci a ukázky pro konkrétního typu poskytovatele LINQ, kterého vás zajímá:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také:

- [Dotaz integrovaný na jazyku (LINQ)C#()](./index.md)
- [Výrazy dotazů LINQ](../../../linq/index.md)

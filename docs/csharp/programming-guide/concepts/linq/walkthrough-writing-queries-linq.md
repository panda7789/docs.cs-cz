---
title: 'Návod: Zápis dotazů v C# (LINQ)'
description: Tento návod ukazuje, jak se ve výrazech dotazů LINQ používají funkce jazyka C#. Tento článek používá Visual Studio jako vývojové prostředí.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: d49cb725c9ce9a417f78f638795e98a75a086893
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302214"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Návod: Zápis dotazů v C# (LINQ)
Tento návod ukazuje funkce jazyka C#, které slouží k zápisu výrazů dotazů LINQ.  
  
## <a name="create-a-c-project"></a>Vytvoření projektu v jazyce C#  
  
> [!NOTE]
> Následující pokyny jsou pro Visual Studio. Pokud používáte jiné vývojové prostředí, vytvořte projekt konzoly s odkazem na System.Core.dll a `using` direktivou pro <xref:System.Linq?displayProperty=nameWithType> obor názvů.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Vytvoření projektu v aplikaci Visual Studio  
  
1. Spusťte Visual Studio.  
  
2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
     Otevře se dialogové okno **Nový projekt** .  
  
3. Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **Visual C#** a pak zvolte možnost **Konzolová aplikace**.  
  
4. Do textového pole **název** zadejte jiný název nebo přijměte výchozí název a pak klikněte na tlačítko **OK** .  
  
     Nový projekt se zobrazí v **Průzkumník řešení**.  
  
5. Všimněte si, že váš projekt má odkaz na System.Core.dll a `using` direktivu pro <xref:System.Linq?displayProperty=nameWithType> obor názvů.  
  
## <a name="create-an-in-memory-data-source"></a>Vytvoření zdroje dat v paměti  
 Zdroj dat pro dotazy je jednoduchý seznam `Student` objektů. Každý `Student` záznam má křestní jméno, příjmení a pole celých čísel, která představují jejich skóre testů ve třídě. Zkopírujte tento kód do projektu. Všimněte si následujících vlastností:  
  
- `Student`Třída se skládá z automaticky implementovaných vlastností.  
  
- Každý student v seznamu se inicializuje s inicializátorem objektu.  
  
- Samotný seznam je inicializován s inicializátorem kolekce.  
  
 Tato Celá datová struktura bude inicializována a vytvořena bez explicitního volání jakéhokoliv konstruktoru nebo explicitního přístupu ke členu. Další informace o těchto nových funkcích naleznete v tématu [automaticky implementované vlastnosti](../../classes-and-structs/auto-implemented-properties.md) a [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
- Přidejte `Student` třídu a inicializovaný seznam studentů do `Program` třídy v projektu.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového objektu Student do seznamu Students  
  
1. Přidejte nový `Student` do `Students` seznamu a použijte název a hodnocení podle vašeho výběru. Zkuste zadat všechny informace o novém studentovi, aby se lépe dozvěděla syntaxe inicializátoru objektu.  
  
## <a name="create-the-query"></a>Vytvoření dotazu  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
- V `Main` metodě aplikace vytvořte jednoduchý dotaz, který při jeho spuštění vytvoří seznam všech studentů, jejichž skóre na prvním testu bylo větší než 90. Všimněte si, že vzhledem k tomu `Student` , že je vybrán celý objekt, je typ dotazu `IEnumerable<Student>` . I když kód může také použít implicitní zadání pomocí klíčového slova [var](../../../language-reference/keywords/var.md) , explicitní psaní se používá k jasné ilustraci výsledků. (Další informace o naleznete `var` v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Všimněte si také, že proměnná rozsahu dotazu `student` slouží jako odkaz na každý `Student` zdroj a poskytuje pro každý objekt přístup pro členy.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Provedení dotazu  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1. Nyní zapište `foreach` smyčku, která způsobí, že se dotaz spustí. Všimněte si následujícího kódu:  
  
    - Každý prvek v vrácené sekvenci je k dispozici prostřednictvím proměnné iterace ve `foreach` smyčce.  
  
    - Typ této proměnné je `Student` a typ proměnné dotazu je kompatibilní, `IEnumerable<Student>` .  
  
2. Po přidání tohoto kódu Sestavte a spusťte aplikaci, abyste viděli výsledky v okně **konzoly** .  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Přidání další podmínky filtru  
  
1. Můžete zkombinovat více logických podmínek v `where` klauzuli, aby bylo možné dále upřesnit dotaz. Následující kód přidá podmínku, takže dotaz vrátí takové studenty, jejichž první skóre bylo nad 90 a jejichž poslední skóre bylo menší než 80. `where`Klauzule by měla vypadat podobně jako následující kód.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Další informace naleznete v tématu [Where klauzule](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Úprava dotazu  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1. Vyhledávání výsledků bude snazší, pokud jsou v nějakém typu pořadí. Vrácenou sekvenci můžete seřadit podle libovolného dostupného pole ve zdrojových prvcích. Například následující `orderby` klauzule seřadí výsledky v abecedním pořadí od A do Z podle příjmení každého studenta. Přidejte `orderby` do dotazu následující klauzuli, a to hned za `where` příkazem a před `select` příkazem:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Nyní změňte `orderby` klauzuli tak, aby odpovídala výsledkům v obráceném pořadí podle skóre prvního testu od nejvyššího skóre po nejnižší skóre.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Změňte `WriteLine` řetězec formátu tak, abyste viděli skóre:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Další informace naleznete v tématu [OrderBy klauzule](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Seskupení výsledků  
  
1. Seskupení je výkonná funkce ve výrazech dotazů. Dotaz s klauzulí GROUP vytvoří posloupnost skupin a každá skupina obsahuje `Key` a sekvenci, která se skládá ze všech členů této skupiny. Následující nové dotazy seskupují studenty pomocí prvního písmene jejich příjmení jako klíče.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Všimněte si, že typ dotazu byl nyní změněn. Nyní vytváří sekvenci skupin, které mají `char` typ jako klíč, a posloupnost `Student` objektů. Vzhledem k tomu, že se typ dotazu změnil, následující kód změní `foreach` smyčku spouštění také:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Spusťte aplikaci a zobrazte výsledky v okně **konzoly** .  
  
     Další informace naleznete v tématu [Group](../../../language-reference/keywords/group-clause.md)Group.  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Převedení proměnných na implicitně typované proměnné  
  
1. Explicitní kódování `IEnumerables` `IGroupings` se může rychle stát zdlouhavě. Stejný dotaz a smyčku můžete napsat `foreach` mnohem přesněji pomocí `var` . `var`Klíčové slovo nemění typy vašich objektů; pouze instruuje kompilátor, aby odvodí typy. Změňte typ `studentQuery` proměnné a proměnnou iterace `group` na `var` a znovu spusťte dotaz. Všimněte si, že ve vnitřní `foreach` smyčce je proměnná iterace stále zadána jako `Student` a dotaz funguje stejně jako předtím. Změňte `s` proměnnou iterace na `var` a spusťte dotaz znovu. Vidíte, že se vám přesně vrátí stejné výsledky.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Další informace o funkci [var](../../../language-reference/keywords/var.md)naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Seřazení skupin podle hodnoty jejich klíče  
  
1. Když spustíte předchozí dotaz, zjistíte, že skupiny nejsou v abecedním pořadí. Chcete-li toto změnit, je nutné zadat `orderby` klauzuli za `group` klauzulí. Chcete-li však použít `orderby` klauzuli, nejprve potřebujete identifikátor, který slouží jako odkaz na skupiny vytvořené `group` klauzulí. Identifikátor můžete zadat pomocí `into` klíčového slova následujícím způsobem:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Když spustíte tento dotaz, uvidíte, že se skupiny teď řadí v abecedním pořadí.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Zavedení identifikátoru s použitím klíčového slova let  
  
1. Klíčové slovo lze použít `let` k zavedení identifikátoru pro jakýkoli výsledek výrazu ve výrazu dotazu. Tento identifikátor může být pohodlí, jak je uvedeno v následujícím příkladu, nebo může zvýšit výkon tím, že uloží výsledky výrazu tak, aby se nemusela vypočítat víckrát.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Další informace naleznete v [klauzuli let](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Použití syntaxe využívající metody ve výrazu dotazu  
  
1. Jak je popsáno v syntaxi [dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md), některé operace dotazu lze vyjádřit pouze pomocí syntaxe metody. Následující kód vypočítá celkové skóre pro každý `Student` ze zdrojových sekvencí a potom zavolá `Average()` metodu pro výsledky tohoto dotazu pro výpočet průměrného skóre třídy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Transformace nebo projekce v klauzuli select  
  
1. Je velmi běžné, že dotaz vytvoří sekvenci, jejíž prvky se liší od prvků ve zdrojových sekvencích. Odstraňte nebo zakomentujte předchozí dotaz a smyčku spuštění a nahraďte ji následujícím kódem. Všimněte si, že dotaz vrátí sekvenci řetězců (ne `Students` ) a tento fakt se projeví ve `foreach` smyčce.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kód uvedený výše v tomto návodu uvádí, že průměrné skóre třídy je přibližně 334. Chcete-li vytvořit sekvenci `Students` , jejichž celkové skóre je větší než průměr třídy, společně s jejich pomocí `Student ID` , můžete v příkazu použít anonymní typ `select` :  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Další kroky  
 Až budete obeznámeni se základními aspekty práce s dotazy v jazyce C#, jste připraveni si přečíst dokumentaci a ukázky pro konkrétního typu poskytovatele LINQ, kterého vás zajímá:  
  
 [Technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také:

- [LINQ (Language-Integrated Query) (C#)](./index.md)
- [Výrazy dotazů LINQ](../../../linq/index.md)

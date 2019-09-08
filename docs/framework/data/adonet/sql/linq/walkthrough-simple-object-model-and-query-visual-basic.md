---
title: 'Návod: Jednoduchý objektový model a dotaz (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: c21a187739ba19be2dc8e89b4dddc94ad799f036
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792119"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Návod: Jednoduchý objektový model a dotaz (Visual Basic)

Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitými složitostmi. Vytvoříte třídu entity, která bude modelem tabulky Customers v ukázkové databázi Northwind. Pak vytvoříte jednoduchý dotaz, který vypíše zákazníky nacházející se v Londýně.

Tento názorný postup je orientovaný na kód, který usnadňuje zobrazení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] konceptů. Normálně řečeno, k vytvoření objektového modelu použijte Návrhář relací objektů.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Tento návod byl napsán pomocí Visual Basic nastavení vývoje.

## <a name="prerequisites"></a>Požadavky

- Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest). Před zahájením tohoto návodu vytvořte tuto složku.

- Tento návod vyžaduje ukázkovou databázi Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft. Pokyny najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md). Po stažení databáze zkopírujte soubor do složky c:\linqtest.

## <a name="overview"></a>Přehled

Tento názorný postup se skládá ze šesti hlavních úloh:

- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.

- Mapování třídy na databázovou tabulku.

- Určení vlastností třídy, které reprezentují sloupce databáze.

- Určuje připojení k databázi Northwind.

- Vytvoření jednoduchého dotazu pro spuštění v databázi.

- Provádění dotazu a sledování výsledků.

## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL

V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.

### <a name="to-create-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL

1. V nabídce **soubor** klikněte na příkaz **Nový projekt**.

2. V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **Visual Basic**.

3. V podokně **šablony** klikněte na **Konzolová aplikace**.

4. Do pole **název** zadejte **LinqConsoleApp**.

5. Klikněte na **OK**.

## <a name="adding-linq-references-and-directives"></a>Přidání odkazů a direktiv LINQ

Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu. Pokud `System.Data.Linq` není v projektu uvedena jako odkaz (klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** a rozbalte uzel **odkazy** ), přidejte jej, jak je vysvětleno v následujícím postupu.

### <a name="to-add-systemdatalinq"></a>Přidání System. data. Linq

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.

     Sestavení je přidáno do projektu.

3. V dialogovém okně **Přidat odkaz** klikněte na **.NET**, přejděte na System. Windows. Forms a klikněte na **OK**.

     Toto sestavení, které podporuje okno se zprávou v návodu, je přidáno do projektu.

4. Níže přidejte následující direktivy `Module1`:

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Mapování třídy na databázovou tabulku

V tomto kroku vytvoříte třídu a namapujete ji na databázovou tabulku. Taková třída je označována jako *Třída entity*. Všimněte si, že mapování je provedeno pouhým přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atributu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Vytvoření třídy entity a její mapování na databázovou tabulku

- Zadejte nebo vložte následující kód do Module1. vb hned výše `Sub Main`:

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Určení vlastností třídy, které reprezentují sloupce databáze

V tomto kroku budete provádět několik úloh.

- Použijte <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k označení `CustomerID` a `City` vlastností třídy entity jako reprezentace sloupců v databázové tabulce.

- Určíte `CustomerID` vlastnost, která představuje sloupec primárního klíče v databázi.

- `_CustomerID` Určíte`_City` pole pro soukromé úložiště. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pak může ukládat a načítat hodnoty přímo místo použití veřejných přístupových objektů, které by mohly zahrnovat obchodní logiku.

### <a name="to-represent-characteristics-of-two-database-columns"></a>Reprezentace vlastností dvou databázových sloupců

- Zadejte nebo vložte následující kód do Module1. vb těsně před `End Class`:

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Určení připojení k databázi Northwind

V tomto kroku použijete <xref:System.Data.Linq.DataContext> objekt k navázání spojení mezi datovými strukturami založenými na kódu a databází samotné. <xref:System.Data.Linq.DataContext> Je hlavním kanálem, přes který načtete objekty z databáze a odešlete změny.

Deklarujete také, `Table(Of Customer)` aby sloužil jako logická, typová tabulka pro dotazy na tabulce Customers v databázi. Tyto dotazy budete vytvářet a spouštět v pozdějších krocích.

### <a name="to-specify-the-database-connection"></a>Určení připojení k databázi

- Do `Sub Main` metody zadejte nebo vložte následující kód.

     Všimněte si, `northwnd.mdf` že se předpokládá, že se soubor nachází ve složce linqtest. Další informace najdete v části požadavky výše v tomto návodu.

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a>Vytvoření jednoduchého dotazu

V tomto kroku vytvoříte dotaz pro vyhledání zákazníků v tabulce Database Customers (zákazníci), kteří se nacházejí v Londýně. Dotazový kód v tomto kroku pouze popisuje dotaz. Nespustí ho. Tento přístup se označuje jako *odložené provádění*. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Vytvoří se také výstup protokolu pro zobrazení příkazů SQL, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generují. Tato funkce protokolování (která používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečná při ladění a při určování, zda jsou příkazy, které jsou odesílány do databáze, přesně reprezentovány vaším dotazem.

### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu

- Zadejte nebo vložte následující kód do `Sub Main` metody `Table(Of Customer)` po deklaraci:

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a>Provádění dotazu

V tomto kroku ve skutečnosti spustíte dotaz. Výrazy dotazu, které jste vytvořili v předchozích krocích, se nevyhodnotí, dokud nebudou nutné výsledky. Po zahájení `For Each` iterace se provede příkaz SQL pro databázi a objekty, které jsou materializované.

### <a name="to-execute-the-query"></a>Provedení dotazu

1. Zadejte nebo vložte následující kód na konec `Sub Main` metody (po popisu dotazu):

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. Pro ladění aplikace stiskněte klávesu F5.

    > [!NOTE]
    > Pokud vaše aplikace vygeneruje chybu za běhu, přečtěte si pokyny v části věnované řešení potíží v tématu [učení](learning-by-walkthroughs.md).

     V okně se zprávou se zobrazí seznam šesti zákazníků. V okně konzoly se zobrazí vygenerovaný kód SQL.

3. Kliknutím na tlačítko **OK** zavřete okno se zprávou.

     Aplikace se zavře.

4. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.

     Pokud budete pokračovat v dalším návodu, budete tuto aplikaci potřebovat.

## <a name="next-steps"></a>Další kroky

[Návod: Dotazování napříč relacemi (Visual Basic](walkthrough-querying-across-relationships-visual-basic.md) ) pokračuje v tom, kde tento návod skončí. Návod pro dotazování napříč relacemi ukazuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , jak se může dotazovat napříč tabulkami, podobně jako *spojení* v relační databázi.

Pokud chcete provést dotazování napříč relacemi, nezapomeňte uložit řešení pro návod, který jste právě dokončili, což je předpoklad.

## <a name="see-also"></a>Viz také:

- [Učení podle návodů](learning-by-walkthroughs.md)

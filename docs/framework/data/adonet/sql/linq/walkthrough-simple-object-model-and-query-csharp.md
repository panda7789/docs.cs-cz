---
title: 'Návod: Jednoduchý objektový model a dotaz (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 43092eb7490d5629f1ababac1d8f8b3aff94299b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971868"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Návod: Jednoduchý objektový model a dotaz (C#)

Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitými složitostmi. Vytvoříte třídu entity, která bude modelem tabulky Customers v ukázkové databázi Northwind. Pak vytvoříte jednoduchý dotaz, který vypíše zákazníky nacházející se v Londýně.

Tento názorný postup je orientovaný na kód, který usnadňuje zobrazení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] konceptů. Normálně řečeno, k vytvoření objektového modelu použijte Návrhář relací objektů.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.

## <a name="prerequisites"></a>Požadavky

- Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest5). Před zahájením tohoto návodu vytvořte tuto složku.

- Tento návod vyžaduje ukázkovou databázi Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft. Pokyny najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze zkopírujte soubor do složky c:\linqtest5.

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

1. V nabídce **soubor** v aplikaci Visual Studio přejděte na **Nový**a klikněte na **projekt**.

2. V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **vizuál C#** .

3. V podokně **šablony** klikněte na **Konzolová aplikace**.

4. Do pole **název** zadejte **LinqConsoleApp**.

5. V poli **umístění** ověřte, kam chcete uložit soubory projektu.

6. Klikněte na **OK**.

## <a name="adding-linq-references-and-directives"></a>Přidání odkazů a direktiv LINQ

Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu. Pokud System. data. Linq není v projektu uveden jako odkaz (rozbalte uzel **odkazy** v **Průzkumník řešení**), přidejte jej, jak je vysvětleno v následujícím postupu.

### <a name="to-add-systemdatalinq"></a>Přidání System. data. Linq

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.

     Sestavení je přidáno do projektu.

3. Do horní části **program.cs**přidejte následující direktivy:

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Mapování třídy na databázovou tabulku

V tomto kroku vytvoříte třídu a namapujete ji na databázovou tabulku. Taková třída je označována jako *Třída entity*. Všimněte si, že mapování je provedeno pouhým přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atributu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Vytvoření třídy entity a její mapování na databázovou tabulku

- Zadejte nebo vložte následující kód do program.cs hned nad `Program` deklaraci třídy:

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Určení vlastností třídy, které reprezentují sloupce databáze

V tomto kroku budete provádět několik úloh.

- Použijte <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k označení `CustomerID` a `City` vlastností třídy entity jako reprezentace sloupců v databázové tabulce.

- Určíte `CustomerID` vlastnost, která představuje sloupec primárního klíče v databázi.

- `_CustomerID` Určíte`_City` pole pro soukromé úložiště. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pak může ukládat a načítat hodnoty přímo místo použití veřejných přístupových objektů, které by mohly zahrnovat obchodní logiku.

### <a name="to-represent-characteristics-of-two-database-columns"></a>Reprezentace vlastností dvou databázových sloupců

- Do program.cs do složených závorek `Customer` třídy zadejte nebo vložte následující kód.

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Určení připojení k databázi Northwind

V tomto kroku použijete <xref:System.Data.Linq.DataContext> objekt k navázání spojení mezi datovými strukturami založenými na kódu a databází samotné. <xref:System.Data.Linq.DataContext> Je hlavním kanálem, přes který načtete objekty z databáze a odešlete změny.

Deklarujete také, `Table<Customer>` aby sloužil jako logická, typová tabulka pro dotazy na tabulce Customers v databázi. Tyto dotazy budete vytvářet a spouštět v pozdějších krocích.

### <a name="to-specify-the-database-connection"></a>Určení připojení k databázi

- Do `Main` metody zadejte nebo vložte následující kód.

     Všimněte si, `northwnd.mdf` že se předpokládá, že se soubor nachází ve složce linqtest5. Další informace najdete v části požadavky výše v tomto návodu.

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a>Vytvoření jednoduchého dotazu

V tomto kroku vytvoříte dotaz pro vyhledání zákazníků v tabulce Database Customers (zákazníci), kteří se nacházejí v Londýně. Dotazový kód v tomto kroku pouze popisuje dotaz. Nespustí ho. Tento přístup se označuje jako *odložené provádění*. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Vytvoří se také výstup protokolu pro zobrazení příkazů SQL, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generují. Tato funkce protokolování (která používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečná při ladění a při určování, zda jsou příkazy, které jsou odesílány do databáze, přesně reprezentovány vaším dotazem.

### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu

- Zadejte nebo vložte následující kód do `Main` metody `Table<Customer>` po deklaraci.

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a>Provádění dotazu

V tomto kroku ve skutečnosti spustíte dotaz. Výrazy dotazu, které jste vytvořili v předchozích krocích, se nevyhodnotí, dokud nebudou nutné výsledky. Po zahájení `foreach` iterace se provede příkaz SQL pro databázi a objekty, které jsou materializované.

### <a name="to-execute-the-query"></a>Provedení dotazu

1. Zadejte nebo vložte následující kód na konec `Main` metody (po popisu dotazu).

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. Pro ladění aplikace stiskněte klávesu F5.

    > [!NOTE]
    >  Pokud vaše aplikace vygeneruje chybu za běhu, přečtěte si pokyny v části věnované řešení potíží v tématu [učení](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).

     Výsledky dotazu v okně konzoly by měly vypadat takto:

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. V okně konzoly stiskněte klávesu ENTER, aby se aplikace zavřela.

## <a name="next-steps"></a>Další kroky

[Návod: Dotazování napříč relacemiC#(](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) ) pokračuje v tom, kde tento návod skončí. Návod dotaz napříč relacemi ukazuje, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jak se může dotazovat napříč tabulkami, podobně jako *spojení* v relační databázi.

Pokud chcete dotaz provést napříč relacemi, nezapomeňte uložit řešení pro návod, který jste právě dokončili, což je předpoklad.

## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)

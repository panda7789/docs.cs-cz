---
title: 'Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 1250f2fe0ccd7661b9bc1986000143ec4a15a9f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053279"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)

LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.

Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server a filtruje výsledky podle konkrétní hodnoty pomocí `Where` klauzule. Další informace naleznete v tématu [Where klauzule](../../../../visual-basic/language-reference/queries/where-clause.md).

V příkladech v tomto tématu se používá ukázková databáze Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a>Vytvoření připojení k databázi

1. V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Průzkumník databáze** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .

2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.

3. Zadejte platné připojení k ukázkové databázi Northwind.

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Přidání projektu, který obsahuje soubor LINQ to SQL

1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**. Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**. Vyberte šablonu položky **LINQ to SQL třídy** .

3. Pojmenujte soubor `northwind.dbml`. Klikněte na **Přidat**. Otevře se Návrhář relací objektů (O/R Designer) pro soubor Northwind. dbml.

## <a name="to-add-tables-to-query-to-the-or-designer"></a>Přidání tabulek pro dotaz do návrháře O/R

1. V Průzkumníku **Průzkumník serveru**/**Database**rozbalte připojení k databázi Northwind. Rozbalte složku **tabulky** .

     Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.

2. Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře. Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.

     Návrhář vytvoří nové `Customer` objekty a `Order` pro váš projekt. Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty. IntelliSense například zobrazí, že `Customer` objekt `Orders` má vlastnost pro všechny objednávky související s tímto zákazníkem.

3. Uložte změny a zavřete návrháře.

4. Uložte projekt.

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Přidání kódu pro dotazování databáze a zobrazení výsledků

1. Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.

2. Poklikejte na Form1 a přidejte kód do `Load` události formuláře.

3. Když jste přidali tabulky do návrháře o/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt pro váš projekt. Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, kromě jednotlivých objektů a kolekcí pro každou tabulku. <xref:System.Data.Linq.DataContext> Objekt pro projekt je pojmenován na základě názvu souboru. dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext`.

    Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazovat se na tabulky určené návrhářem o/R.

    Do `Load` události přidejte následující kód pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti vašeho kontextu dat. Dotaz vyfiltruje výsledky a vrátí pouze zákazníky nacházející se v `London`.

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.

5. Níže jsou uvedeny některé další filtry, které můžete vyzkoušet.

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)

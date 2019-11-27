---
title: 'Postupy: počítání, suma nebo průměr dat pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345013"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)
LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server. Počet vzorků, součty a průměrují výsledky pomocí klauzulí `Aggregate` a `Group By`. Další informace naleznete v tématu [klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 V příkladech v tomto tématu se používá ukázková databáze Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Vytvoření připojení k databázi  
  
1. V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Database explorer** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .  
  
2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.  
  
3. Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Přidání projektu, který obsahuje soubor LINQ to SQL  
  
1. V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**. Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .  
  
2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**. Vyberte šablonu položky **LINQ to SQL třídy** .  
  
3. Pojmenujte soubor `northwind.dbml`. Klikněte na tlačítko **Přidat**. Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Přidání tabulek pro dotaz do návrháře O/R  
  
1. V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind. Rozbalte složku **tabulky** .  
  
     Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.  
  
2. Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře. Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.  
  
     Návrhář vytvoří nový objekt `Customer` a objekty `Order` pro váš projekt. Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty. IntelliSense například zobrazí, že objekt `Customer` má vlastnost `Orders` pro všechny objednávky související s tímto zákazníkem.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Přidání kódu pro dotazování databáze a zobrazení výsledků  
  
1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.  
  
2. Poklikejte na Form1 a přidejte kód do události `Load` formuláře.  
  
3. Když jste přidali tabulky do návrháře pro/R, Návrhář přidal objekt <xref:System.Data.Linq.DataContext> pro váš projekt. Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, a pro přístup k jednotlivým objektům a kolekcím pro každou tabulku. Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml. Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> ve vašem kódu a dotazovat tabulky určené návrhářem O/R.  
  
     Přidejte následující kód do události `Load` pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti <xref:System.Data.Linq.DataContext> a počet, součet a průměr výsledků. Ukázka používá klauzuli `Aggregate` pro dotazování na jeden výsledek a klauzuli `Group By` pro zobrazení průměru pro seskupené výsledky.  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)

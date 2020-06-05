---
title: 'Postupy: Vrácení výsledku dotazu LINQ jako specifického typu'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404949"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)
LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů. Ve výchozím nastavení dotazy LINQ vrátí seznam objektů jako anonymní typ. Můžete také určit, že dotaz vrátí seznam konkrétního typu pomocí `Select` klauzule.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server a projekty výsledky jako konkrétní pojmenovaný typ. Další informace naleznete v tématu [anonymní typy](../objects-and-classes/anonymous-types.md) a [klauzule SELECT](../../../language-reference/queries/select-clause.md).  
  
 V příkladech v tomto tématu se používá ukázková databáze Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Vytvoření připojení k databázi  
  
1. V aplikaci Visual Studio otevřete **Průzkumník serveru** / **Průzkumník databáze** kliknutím na **Průzkumník serveru** / **Průzkumník databáze** v nabídce **zobrazení** .  
  
2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru** / **Průzkumníku databáze** a pak klikněte na **Přidat připojení**.  
  
3. Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Přidání projektu, který obsahuje soubor LINQ to SQL  
  
1. V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**. Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .  
  
2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**. Vyberte šablonu položky **LINQ to SQL třídy** .  
  
3. Pojmenujte soubor `northwind.dbml`. Klikněte na tlačítko **Add** (Přidat). Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Přidání tabulek pro dotaz do návrháře O/R  
  
1. V **Server Explorer** / **Průzkumníku Průzkumník serveru Database**rozbalte připojení k databázi Northwind. Rozbalte složku **tabulky** .  
  
     Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.  
  
2. Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.  
  
     Návrhář vytvoří nový `Customer` objekt pro váš projekt. Výsledek dotazu můžete promítnout jako `Customer` typ nebo jako typ, který vytvoříte. Tato ukázka vytvoří nový typ v pozdější proceduře a projekt výsledek dotazu jako tento typ.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Přidání kódu pro dotazování databáze a zobrazení výsledků  
  
1. Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.  
  
2. Poklikejte na Form1 a upravte třídu Form1.  
  
3. Po `End Class` příkazu třídy Form1 přidejte následující kód, který vytvoří `CustomerInfo` typ pro uložení výsledků dotazu pro tuto ukázku.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. Když jste přidali tabulky do návrháře O/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt do projektu. Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, a pro přístup k jednotlivým objektům a kolekcím pro každou tabulku. <xref:System.Data.Linq.DataContext>Objekt pro projekt je pojmenován na základě názvu souboru. dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext` .  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazovat se na tabulky určené návrhářem o/R.  
  
     V `Load` případě třídy Form1 přidejte následující kód pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti vašeho kontextu dat. `Select`Klauzule dotazu vytvoří nový `CustomerInfo` typ namísto anonymního typu pro každou položku výsledku dotazu.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.  
  
## <a name="see-also"></a>Viz také

- [LINQ](index.md)
- [Dotazy](../../../language-reference/queries/index.md)
- [Technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)

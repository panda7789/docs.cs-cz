---
title: 'Postupy: volání uložené procedury pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345024"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)
LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi, včetně databázových objektů, jako jsou například uložené procedury.  
  
 Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi SQL Server. Ukázka ukazuje, jak volat dva různé uložené procedury v databázi. Každý postup vrátí výsledky dotazu. Jeden postup přebírá vstupní parametry a druhý postup nepřijímá parametry.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Přidání uložených procedur do návrháře relací výstupů  
  
1. V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind. Rozbalte složku **uložené procedury** .  
  
     Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.  
  
2. Klikněte na uloženou proceduru **prodej podle roku** a přetáhněte ji do pravého podokna návrháře. Klikněte na **desítkovou** uloženou proceduru, kterou si můžete přetáhnout do pravého podokna návrháře.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Chcete-li přidat kód pro zobrazení výsledků uložených procedur  
  
1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.  
  
2. Poklikejte na Form1 a přidejte do události `Load` kód.  
  
3. Když jste přidali uložené procedury do návrháře O/R, Návrhář přidal objekt <xref:System.Data.Linq.DataContext> pro váš projekt. Tento objekt obsahuje kód, který musíte mít pro přístup k těmto postupům. Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml. Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volat metody uložené procedury určené návrhářem O/R. Chcete-li vytvořit propojení s objektem <xref:System.Windows.Forms.DataGridView>, bude pravděpodobně nutné vynutit okamžité provedení dotazu voláním metody <xref:System.Linq.Enumerable.ToList%2A> u výsledků uložené procedury.  
  
     Do události `Load` přidejte následující kód, který zavolá jeden z uložených procedur vystavených jako metody pro váš datový kontext.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

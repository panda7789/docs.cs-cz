---
title: Práce se soubory a adresáře v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 4d0aac533759f8cc20ac4f19d7f0e49fef17bf56
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314682"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Návod: Práce se soubory a adresáře v jazyce Visual Basic
Tento názorný postup obsahuje úvod do základní informace o souboru vstupně-výstupních operací v jazyce Visual Basic. Popisuje postup vytvoření malou aplikaci, která obsahuje seznam a zkoumá textových souborů v adresáři. Pro každý soubor vybraný text aplikace poskytuje atributy souboru a prvního řádku obsahu. Je k dispozici možnost při zápisu informací do souboru protokolu.  
  
 Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v jazyce Visual Basic. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na konci tohoto průvodce, ekvivalentem příkladu je zadána, který používá třídy z <xref:System.IO> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. Na **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt**.  
  
2. V **nainstalované šablony** podokně rozbalte **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**. V **šablony** podokně kliknout prostředním tlačítkem myši, **formulářová aplikace Windows**.  
  
3. V **název** zadejte `FileExplorer` název projektu a potom klikněte na **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení**, a otevře se Návrhář formulářů Windows.  
  
4. Přidat ovládací prvky do formuláře v následující tabulce a nastavit odpovídající hodnoty pro jejich vlastností.  
  
    |Control|Vlastnost|Value|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Name**|`filesListBox`|  
    |**Tlačítko**|**Name**<br /><br /> **Text**|`browseButton`<br /><br /> **Procházet**|  
    |**Tlačítko**|**Name**<br /><br /> **Text**|`examineButton`<br /><br /> **Prozkoumat**|  
    |**CheckBox**|**Name**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Uložit výsledky**|  
    |**FolderBrowserDialog**|**Name**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Vyberte složku, a seznam souborů ve složce  
  
1. Vytvoření `Click` obslužné rutiny události pro `browseButton` dvojitým kliknutím na ovládací prvek na formuláři. Otevře se Editor kódu.  
  
2. Přidejte následující kód, který `Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog` Volání otevře **vyhledat složku** dialogové okno. Když uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnosti je předána jako argument pro `ListFiles` metoda, která se přidá v dalším kroku.  
  
3. Přidejte následující `ListFiles` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Tento kód nejprve vymaže **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pak načte kolekci řetězců, jeden pro každý soubor v adresáři. `GetFiles` Metoda přijímá argument vzor hledání pro načtení souborů vyhovujících určitému vzoru. V tomto příkladu jsou vráceny pouze soubory, které mají příponu .txt.  
  
     Řetězce, které jsou vrácené `GetFiles` metoda se poté přidají ke **ListBox**.  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet** tlačítko. V **vyhledat složku** dialogovém okně, přejděte do složky, která obsahuje soubory s příponou .txt, a potom vyberte složku a klikněte na **OK**.  
  
     `ListBox` Obsahuje seznam souborů .txt ve vybrané složce.  
  
5. Zastavení, spuštění aplikace.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Získání atributů souboru a obsahu z textového souboru  
  
1. Vytvoření `Click` obslužné rutiny události pro `examineButton` dvojitým kliknutím na ovládací prvek na formuláři.  
  
2. Přidejte následující kód, který `Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kód zkontroluje, zda je položka vybrána v `ListBox`. Potom získá položka z cesty k souboru `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda se používá ke kontrole, jestli soubor stále existuje.  
  
     Cesta k souboru je předána jako argument pro `GetTextForOutput` metoda, která se přidá v dalším kroku. Tato metoda vrátí řetězec, který obsahuje informace o souboru. Informace o souboru se zobrazí v **MessageBox**.  
  
3. Přidejte následující `GetTextForOutput` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Tento kód použije <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metoda získat soubor parametrů. Soubor parametrů jsou přidány do <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Přečte obsah souboru do metody <xref:System.IO.StreamReader>. První řádek obsah se získávají z `StreamReader` a je přidán `StringBuilder`.  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet**a přejděte do složky obsahující soubory s příponou .txt. Klikněte na **OK**.  
  
     Vyberte soubor v `ListBox`a potom klikněte na tlačítko **vyhledejte**. A `MessageBox` zobrazuje informace o souboru.  
  
5. Zastavení, spuštění aplikace.  
  
### <a name="to-add-a-log-entry"></a>Chcete-li přidat položky protokolu  
  
1. Přidejte následující kód do konce `examineButton_Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu ve stejném adresáři jako u vybraného souboru. Text položky protokolu nastavena na aktuální datum a čas, za nímž následuje informace o souboru.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody s `append` argument nastaven na `True`, se používá k vytvoření položky protokolu.  
  
2. Spusťte aplikaci. Přejděte do textového souboru, vyberte ho v `ListBox`, vyberte **uložit výsledky** zaškrtněte políčko a potom klikněte na tlačítko **vyhledejte**. Ověřte, že záznam protokolu se zapisují na `log.txt` souboru.  
  
3. Zastavení, spuštění aplikace.  
  
### <a name="to-use-the-current-directory"></a>Chcete-li používat aktuální adresář  
  
1. Vytvořte obslužnou rutinu události pro `Form1_Load` poklepáním na formuláři.  
  
2. Přidejte následující kód do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Tento kód nastaví výchozí adresář prohlížeč složek do aktuálního adresáře.  
  
3. Spusťte aplikaci. Po kliknutí na **Procházet** poprvé, **vyhledat složku** dialogové okno k aktuálnímu adresáři.  
  
4. Zastavení, spuštění aplikace.  
  
### <a name="to-selectively-enable-controls"></a>Povolit některé ovládací prvky  
  
1. Přidejte následující `SetEnabled` metody.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled` Metoda povolí nebo zakáže ovládací prvky v závislosti na tom, zda je položka vybrána v `ListBox`.  
  
2. Vytvoření `SelectedIndexChanged` obslužné rutiny události pro `filesListBox` dvojitým kliknutím `ListBox` ovládací prvek na formuláři.  
  
3. Přidejte volání do `SetEnabled` na novém `filesListBox_SelectedIndexChanged` obslužné rutiny události.  
  
4. Přidejte volání do `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.  
  
5. Přidejte volání do `SetEnabled` na konci `Form1_Load` obslužné rutiny události.  
  
6. Spusťte aplikaci. **Uložit výsledky** zaškrtávací políčko a **vyhledejte** tlačítka jsou zakázané, pokud položka není vybraný `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Úplný příklad použití My.Computer.FileSystem  
 Následuje Úplný příklad.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Úplný příklad using System.IO  
 Následující příklad ekvivalentní používá třídy z <xref:System.IO> obor názvů namísto použití `My.Computer.FileSystem` objekty.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Návod: Práce se soubory pomocí metod rozhraní .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

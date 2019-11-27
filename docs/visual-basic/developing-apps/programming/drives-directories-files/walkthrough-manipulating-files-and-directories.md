---
title: Práce se soubory a adresáři
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
ms.openlocfilehash: 83dc6ce0d29c1c368c36b51fc84ecad34d72e01f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333810"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Návod: Práce se soubory a adresáři v jazyce Visual Basic

V tomto návodu se seznámíte se základy vstupně-výstupních operací se soubory v Visual Basic. Popisuje, jak vytvořit malou aplikaci, která zobrazí a prověřuje textové soubory v adresáři. Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu. K dispozici je možnost zápisu informací do souboru protokolu.  
  
 Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v Visual Basic. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na konci tohoto návodu je k dispozici podobný příklad, který používá třídy z oboru názvů <xref:System.IO>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. V nabídce **soubor** klikněte na příkaz **Nový projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt** .  
  
2. V podokně **Nainstalované šablony** rozbalte **Visual Basic**a pak klikněte na **Windows**. V podokně **šablony** uprostřed klikněte na **model Windows Forms aplikace**.  
  
3. Do pole **název** zadejte `FileExplorer` pro nastavení názvu projektu a pak klikněte na **OK**.  
  
     Visual Studio přidá projekt do **Průzkumník řešení**a otevře se Návrhář formulářů.  
  
4. Přidejte ovládací prvky z následující tabulky do formuláře a nastavte odpovídající hodnoty jejich vlastností.  
  
    |Ovládací prvek|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Jméno**|`filesListBox`|  
    |**Tlačítko**|**Jméno**<br /><br /> **Text**|`browseButton`<br /><br /> **Hlíží**|  
    |**Tlačítko**|**Jméno**<br /><br /> **Text**|`examineButton`<br /><br /> **Zkontrolujte**|  
    |**CheckBox**|**Jméno**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Uložit výsledky**|  
    |**FolderBrowserDialog**|**Jméno**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Výběr složky a vypsání souborů ve složce  
  
1. Vytvořte obslužnou rutinu události `Click` pro `browseButton` dvojitým kliknutím na ovládací prvek ve formuláři. Otevře se Editor kódu.  
  
2. Do obslužné rutiny události `Click` přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     Volání `FolderBrowserDialog1.ShowDialog` otevře dialogové okno **Vyhledat složku** . Poté, co uživatel klikne na **tlačítko OK**, je vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> odeslána jako argument metodě `ListFiles`, která je přidána v dalším kroku.  
  
3. Přidejte následující metodu `ListFiles`.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Tento kód nejprve vymaže **seznam**.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> potom načte kolekci řetězců, jednu pro každý soubor v adresáři. Metoda `GetFiles` akceptuje argument vyhledávacího vzoru pro načtení souborů, které odpovídají konkrétnímu vzoru. V tomto příkladu jsou vráceny pouze soubory, které mají příponu. txt.  
  
     Řetězce, které jsou vráceny metodou `GetFiles`, jsou poté **přidány do seznamu.**  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet** . V dialogovém okně **Vyhledat složku** přejděte do složky, která obsahuje soubory. txt, a pak vyberte složku a klikněte na **OK**.  
  
     `ListBox` obsahuje seznam souborů. txt ve vybrané složce.  
  
5. Zastavit běh aplikace  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Získání atributů souboru a obsahu z textového souboru  
  
1. Vytvořte obslužnou rutinu události `Click` pro `examineButton` dvojitým kliknutím na ovládací prvek ve formuláři.  
  
2. Do obslužné rutiny události `Click` přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kód ověřuje, zda je položka vybrána v `ListBox`. Poté získá položku cesty k souboru z `ListBox`. Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> slouží ke kontrole, zda soubor stále existuje.  
  
     Cesta k souboru je odeslána jako argument metody `GetTextForOutput`, která je přidána v dalším kroku. Tato metoda vrátí řetězec, který obsahuje informace o souboru. Informace o souboru se zobrazí v **MessageBox**.  
  
3. Přidejte následující metodu `GetTextForOutput`.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kód používá metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> k získání parametrů souboru. Parametry souboru jsou přidány do <xref:System.Text.StringBuilder>.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> přečte obsah souboru do <xref:System.IO.StreamReader>. První řádek obsahu se získá z `StreamReader` a přidá se do `StringBuilder`.  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory. txt. Klikněte na tlačítko **OK**.  
  
     Vyberte soubor v `ListBox`a pak klikněte na **prošetřit**. `MessageBox` zobrazí informace o souboru.  
  
5. Zastavit běh aplikace  
  
### <a name="to-add-a-log-entry"></a>Přidání položky protokolu  
  
1. Přidejte následující kód na konec obslužné rutiny události `examineButton_Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu do stejného adresáře jako u vybraného souboru. Text položky protokolu je nastaven na aktuální datum a čas, po kterém následují informace o souboru.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> s argumentem `append` nastaveným na `True`slouží k vytvoření položky protokolu.  
  
2. Spusťte aplikaci. Přejděte k textovému souboru, vyberte ho v `ListBox`, zaškrtněte políčko **Uložit výsledky** a potom klikněte na **prošetřit**. Ověřte, že položka protokolu je zapsána do souboru `log.txt`.  
  
3. Zastavit běh aplikace  
  
### <a name="to-use-the-current-directory"></a>Použití aktuálního adresáře  
  
1. Vytvořte obslužnou rutinu události pro `Form1_Load` dvojitým kliknutím na formulář.  
  
2. Přidejte následující kód do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.  
  
3. Spusťte aplikaci. Když kliknete na tlačítko **Procházet** poprvé, otevře se dialogové okno **Vyhledat složku** do aktuálního adresáře.  
  
4. Zastavit běh aplikace  
  
### <a name="to-selectively-enable-controls"></a>Selektivní povolení ovládacích prvků  
  
1. Přidejte následující metodu `SetEnabled`.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     Metoda `SetEnabled` povoluje nebo zakazuje ovládací prvky v závislosti na tom, zda je položka vybrána v `ListBox`.  
  
2. Vytvořte obslužnou rutinu události `SelectedIndexChanged` pro `filesListBox` dvojitým kliknutím na ovládací prvek `ListBox` ve formuláři.  
  
3. Přidejte volání `SetEnabled` v nové obslužné rutině události `filesListBox_SelectedIndexChanged`.  
  
4. Přidejte volání `SetEnabled` na konci obslužné rutiny události `browseButton_Click`.  
  
5. Přidejte volání `SetEnabled` na konci obslužné rutiny události `Form1_Load`.  
  
6. Spusťte aplikaci. Zaškrtávací políčko **Uložit výsledky** a tlačítko **Prohledat** jsou zakázány, pokud položka není vybrána v `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Úplný příklad použití My. Computer. FileSystem  

 Toto je kompletní příklad.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Úplný příklad použití System.IO  

 Následující podobný příklad používá třídy z oboru názvů <xref:System.IO> namísto použití objektů `My.Computer.FileSystem`.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Návod: Práce se soubory pomocí metod rozhraní .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

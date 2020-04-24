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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333810"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Návod: Práce se soubory a adresáři v jazyce Visual Basic

V tomto návodu se seznámíte se základy vstupně-výstupních operací se soubory v Visual Basic. Popisuje, jak vytvořit malou aplikaci, která zobrazí a prověřuje textové soubory v adresáři. Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu. K dispozici je možnost zápisu informací do souboru protokolu.  
  
 Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v Visual Basic. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na konci tohoto návodu je k dispozici podobný příklad, který používá třídy z <xref:System.IO> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. V nabídce **soubor** klikněte na příkaz **Nový projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt**.  
  
2. V podokně **Nainstalované šablony** rozbalte **Visual Basic**a pak klikněte na **Windows**. V podokně **šablony** uprostřed klikněte na **model Windows Forms aplikace**.  
  
3. Do pole **název** zadejte `FileExplorer` název projektu a klikněte na tlačítko **OK**.  
  
     Visual Studio přidá projekt do **Průzkumník řešení**a otevře se Návrhář formulářů.  
  
4. Přidejte ovládací prvky z následující tabulky do formuláře a nastavte odpovídající hodnoty jejich vlastností.  
  
    |Řízení|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Název**|`filesListBox`|  
    |**Tlačítko**|**Název**<br /><br /> **Text**|`browseButton`<br /><br /> **Procházet**|  
    |**Tlačítko**|**Název**<br /><br /> **Text**|`examineButton`<br /><br /> **Zkontrolujte**|  
    |**CheckBox**|**Název**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Uložit výsledky**|  
    |**FolderBrowserDialog**|**Název**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Výběr složky a vypsání souborů ve složce  
  
1. Vytvořte obslužnou `Click` rutinu události `browseButton` pro dvojitým kliknutím na ovládací prvek ve formuláři. Otevře se Editor kódu.  
  
2. Přidejte následující kód do obslužné rutiny `Click` události.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     `FolderBrowserDialog1.ShowDialog` Volání otevře dialogové okno **Vyhledat složku** . Poté, co uživatel klikne na <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> **tlačítko OK**, je vlastnost odeslána jako argument `ListFiles` metodě, která je přidána v dalším kroku.  
  
3. Přidejte následující `ListFiles` metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Tento kód nejprve vymaže **seznam**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda potom načte kolekci řetězců, jednu pro každý soubor v adresáři. `GetFiles` Metoda přijímá argument vzor hledání, který načte soubory, které odpovídají konkrétnímu vzoru. V tomto příkladu jsou vráceny pouze soubory, které mají příponu. txt.  
  
     Řetězce, které jsou vráceny `GetFiles` metodou, jsou poté přidány do seznamu. **ListBox**  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet** . V dialogovém okně **Vyhledat složku** přejděte do složky, která obsahuje soubory. txt, a pak vyberte složku a klikněte na **OK**.  
  
     `ListBox` Obsahuje seznam souborů. txt ve vybrané složce.  
  
5. Zastavit běh aplikace  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Získání atributů souboru a obsahu z textového souboru  
  
1. Vytvořte obslužnou `Click` rutinu události `examineButton` pro dvojitým kliknutím na ovládací prvek ve formuláři.  
  
2. Přidejte následující kód do obslužné rutiny `Click` události.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kód ověřuje, zda je položka vybrána v `ListBox`. Pak získá položku cesty k souboru z `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda slouží ke kontrole, zda soubor stále existuje.  
  
     Cesta k souboru je odeslána jako argument `GetTextForOutput` metodě, která je přidána v dalším kroku. Tato metoda vrátí řetězec, který obsahuje informace o souboru. Informace o souboru se zobrazí v **MessageBox**.  
  
3. Přidejte následující `GetTextForOutput` metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodu pro získání parametrů souboru. Parametry souboru jsou přidány do <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda načte obsah souboru do <xref:System.IO.StreamReader>. První řádek obsahu je získán z `StreamReader` a je přidán do. `StringBuilder`  
  
4. Spusťte aplikaci. Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory. txt. Klikněte na tlačítko **OK**.  
  
     Vyberte soubor v `ListBox`nástroji a klikněte na tlačítko **Prohledat**. A `MessageBox` zobrazuje informace o souboru.  
  
5. Zastavit běh aplikace  
  
### <a name="to-add-a-log-entry"></a>Přidání položky protokolu  
  
1. Přidejte následující kód na konec obslužné rutiny `examineButton_Click` události.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kód nastaví cestu k souboru protokolu pro umístění souboru protokolu do stejného adresáře jako u vybraného souboru. Text položky protokolu je nastaven na aktuální datum a čas, po kterém následují informace o souboru.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda s `append` argumentem nastaveným na `True`slouží k vytvoření položky protokolu.  
  
2. Spusťte aplikaci. Přejděte k textovému souboru, vyberte ho v oblasti `ListBox`, zaškrtněte políčko **Uložit výsledky** a potom klikněte na **prošetřit**. Ověřte, že položka protokolu je zapsána `log.txt` do souboru.  
  
3. Zastavit běh aplikace  
  
### <a name="to-use-the-current-directory"></a>Použití aktuálního adresáře  
  
1. Vytvořte obslužnou rutinu události `Form1_Load` pro dvojitým kliknutím na formulář.  
  
2. Přidejte následující kód do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.  
  
3. Spusťte aplikaci. Když kliknete na tlačítko **Procházet** poprvé, otevře se dialogové okno **Vyhledat složku** do aktuálního adresáře.  
  
4. Zastavit běh aplikace  
  
### <a name="to-selectively-enable-controls"></a>Selektivní povolení ovládacích prvků  
  
1. Přidejte následující `SetEnabled` metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     `SetEnabled` Metoda povoluje nebo zakazuje ovládací prvky v závislosti na tom, zda je položka vybrána `ListBox`v.  
  
2. Vytvořte obslužnou `SelectedIndexChanged` rutinu události `filesListBox` pro dvojitým kliknutím na `ListBox` ovládací prvek ve formuláři.  
  
3. Přidejte volání do `SetEnabled` nové `filesListBox_SelectedIndexChanged` obslužné rutiny události.  
  
4. Na konec obslužné rutiny `SetEnabled` `browseButton_Click` události přidejte volání.  
  
5. Na konec obslužné rutiny `SetEnabled` `Form1_Load` události přidejte volání.  
  
6. Spusťte aplikaci. Zaškrtávací políčko **Uložit výsledky** a tlačítko **prostudovat** jsou zakázány, pokud položka není vybrána v `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Úplný příklad použití My. Computer. FileSystem  

 Toto je kompletní příklad.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Úplný příklad použití System.IO  

 Následující podobný příklad používá třídy z <xref:System.IO> oboru názvů namísto použití `My.Computer.FileSystem` objektů.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

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

Tento návod poskytuje úvod k základům vstupně-videa souboru v jazyce Visual Basic. Popisuje, jak vytvořit malou aplikaci, která uvádí a zkoumá textové soubory v adresáři. Pro každý vybraný textový soubor aplikace poskytuje atributy souboru a první řádek obsahu. Existuje možnost zapsat informace do souboru protokolu.  
  
 Tento návod používá členy `My.Computer.FileSystem Object`, které jsou k dispozici v jazyce Visual Basic. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na konci návodu je k dispozici ekvivalentní příklad, který <xref:System.IO> používá třídy z oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1. V nabídce **Soubor** klepněte na položku **Nový projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt**.  
  
2. V podokně **Nainstalované šablony** rozbalte **položku Visual Basic**a klepněte na tlačítko **Windows**. V podokně **Šablony** uprostřed klepněte na **položku Aplikace Windows Forms Application**.  
  
3. Do pole **Název** `FileExplorer` nastavte název projektu a klepněte na tlačítko **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení**a otevře se Návrhář formulářů systému Windows.  
  
4. Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.  
  
    |Řízení|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Název**|`filesListBox`|  
    |**Tlačítko**|**Název**<br /><br /> **Text**|`browseButton`<br /><br /> **Procházet**|  
    |**Tlačítko**|**Název**<br /><br /> **Text**|`examineButton`<br /><br /> **Zkoumat**|  
    |**CheckBox**|**Název**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Uložit výsledky**|  
    |**Dialogové okno Prohlížeče složek**|**Název**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Výběr složky a seznam souborů ve složce  
  
1. Vytvořte `Click` obslužnou rutinu události `browseButton` poklepáním na ovládací prvek ve formuláři. Otevře se Editor kódu.  
  
2. Přidejte následující kód `Click` do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     Volání `FolderBrowserDialog1.ShowDialog` otevře dialogové okno **Vyhledat složku.** Po kliknutí uživatele **OK**na <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> OK je vlastnost odeslána `ListFiles` jako argument metodě, která je přidána v dalším kroku.  
  
3. Přidejte `ListFiles` následující metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     Tento kód nejprve vymaže **ListBox**.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> pak načte kolekci řetězců, jeden pro každý soubor v adresáři. Metoda `GetFiles` přijímá argument vzor hledání k načtení souborů, které odpovídají určitému vzoru. V tomto příkladu jsou vráceny pouze soubory, které mají příponu TXT.  
  
     Řetězce, které jsou vráceny `GetFiles` metodou jsou pak přidány do **ListBox**.  
  
4. Spusťte aplikaci. Klepněte na tlačítko **Procházet.** V dialogovém okně **Vyhledat složku** vyhledejte složku, která obsahuje soubory TXT, a pak ji vyberte a klepněte na tlačítko **OK**.  
  
     Obsahuje `ListBox` seznam souborů TXT ve vybrané složce.  
  
5. Zastavte spouštění aplikace.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Získání atributů souboru a obsahu z textového souboru  
  
1. Vytvořte `Click` obslužnou rutinu události `examineButton` poklepáním na ovládací prvek ve formuláři.  
  
2. Přidejte následující kód `Click` do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     Kód ověří, zda je položka `ListBox`vybrána v oblasti . Poté získá položku cesty k `ListBox`souboru z . Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> se používá ke kontrole, zda soubor stále existuje.  
  
     Cesta k souboru je odeslána jako argument k metodě, `GetTextForOutput` která je přidána v dalším kroku. Tato metoda vrátí řetězec, který obsahuje informace o souboru. Informace o souboru se zobrazí v **messageboxu**.  
  
3. Přidejte `GetTextForOutput` následující metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metodu k získání parametrů souboru. Parametry souboru jsou <xref:System.Text.StringBuilder>přidány do aplikace .  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> přečte obsah souboru <xref:System.IO.StreamReader>do . První řádek obsahu je získán `StreamReader` z a je `StringBuilder`přidán do .  
  
4. Spusťte aplikaci. Klepněte na **tlačítko Procházet**a vyhledejte složku, která obsahuje soubory TXT. Klikněte na tlačítko **OK**.  
  
     Vyberte soubor `ListBox`v souboru a klepněte na tlačítko **Prozkoumat**. A `MessageBox` zobrazí informace o souboru.  
  
5. Zastavte spouštění aplikace.  
  
### <a name="to-add-a-log-entry"></a>Přidání položky protokolu  
  
1. Přidejte následující kód na `examineButton_Click` konec obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     Kód nastaví cestu k souboru protokolu tak, aby byl soubor protokolu umístěn do stejného adresáře jako vybraný soubor. Text položky protokolu je nastaven na aktuální datum a čas následovaný informacemi o souboru.  
  
     Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> s argumentem `append` nastaveným na `True`, se používá k vytvoření položky protokolu.  
  
2. Spusťte aplikaci. Vyhledejte textový soubor, zaškrtněte `ListBox`v poli , zaškrtněte políčko **Uložit výsledky** a klepněte na tlačítko **Zkontrolovat**. Ověřte, zda je `log.txt` položka protokolu zapsána do souboru.  
  
3. Zastavte spouštění aplikace.  
  
### <a name="to-use-the-current-directory"></a>Použití aktuálního adresáře  
  
1. `Form1_Load` Poklepáním na formulář vytvořte obslužnou rutinu události.  
  
2. Přidejte následující kód do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     Tento kód nastaví výchozí adresář prohlížeče složek na aktuální adresář.  
  
3. Spusťte aplikaci. Po prvním **klepnutí** se otevře dialogové okno **Vyhledat složku** v aktuálním adresáři.  
  
4. Zastavte spouštění aplikace.  
  
### <a name="to-selectively-enable-controls"></a>Chcete-li selektivně povolit kontroly  
  
1. Přidejte `SetEnabled` následující metodu.  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     Metoda `SetEnabled` povolí nebo zakáže ovládací prvky v `ListBox`závislosti na tom, zda je položka vybrána v rozhraní .  
  
2. Vytvořte `SelectedIndexChanged` obslužnou rutinu události `filesListBox` poklepáním na `ListBox` ovládací prvek ve formuláři.  
  
3. Přidejte volání `SetEnabled` do `filesListBox_SelectedIndexChanged` nové obslužné rutiny události.  
  
4. Přidejte volání `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.  
  
5. Přidejte volání `SetEnabled` na konci `Form1_Load` obslužné rutiny události.  
  
6. Spusťte aplikaci. Zaškrtávací políčko **Uložit výsledky** a tlačítko **Zkontrolovat** je zakázáno, pokud v aplikaci není vybraná `ListBox`položka.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Úplný příklad pomocí my.computer.filesystem  

 Následuje úplný příklad.  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a>Úplný příklad pomocí System.IO  

 Následující ekvivalentní příklad používá <xref:System.IO> třídy z `My.Computer.FileSystem` oboru názvů namísto použití objektů.  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

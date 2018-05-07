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
ms.openlocfilehash: ab1c119d2c5cd9bfa0ff725774144bc65817cad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Návod: Práce se soubory a adresáři v jazyce Visual Basic
Tento názorný postup obsahuje úvod do základní informace o souboru vstupně-výstupních operací v jazyce Visual Basic. Popisuje postup vytvoření malé aplikace, která obsahuje seznam a prověří textové soubory v adresáři. Pro každý soubor vybraný text aplikace poskytuje atributy souboru a prvního řádku obsahu. Je k dispozici možnost při zápisu informací do souboru protokolu.  
  
 Tento návod používá členy `My.Computer.FileSystem Object`, které jsou dostupné v jazyce Visual Basic. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.FileIO.FileSystem>. Na konci tohoto průvodce, je ekvivalentní například zadaný používající třídy z <xref:System.IO> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový projekt**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V **nainstalovaných šablonách** podokně rozbalte **jazyka Visual Basic**a potom klikněte na **Windows**. V **šablony** podokně v prostředním, klikněte na **formulářové aplikace Windows**.  
  
3.  V **název** zadejte `FileExplorer` nastavit název projektu a klikněte na tlačítko **OK**.  
  
     Visual Studio. přidá projekt **Průzkumníku**, a otevře v Návrháři formulářů Windows.  
  
4.  Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.  
  
    |Ovládací prvek|Vlastnost|Hodnota|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Jméno**|`filesListBox`|  
    |**Tlačítko**|**Jméno**<br /><br /> **Text**|`browseButton`<br /><br /> **Procházet**|  
    |**Tlačítko**|**Jméno**<br /><br /> **Text**|`examineButton`<br /><br /> **Zkontrolujte**|  
    |**CheckBox**|**Jméno**<br /><br /> **Text**|`saveCheckBox`<br /><br /> **Uložení výsledků**|  
    |**FolderBrowserDialog –**|**Jméno**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Vyberte složku, a seznam souborů ve složce  
  
1.  Vytvoření `Click` obslužné rutiny události pro `browseButton` poklepáním na ovládací prvek na formuláři. Otevře se Editor kódu.  
  
2.  Přidejte následující kód, který `Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` Volání otevře **vyhledat složku** dialogové okno. Poté, co uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost je odeslán jako argument k `ListFiles` metoda, která se přidá v dalším kroku.  
  
3.  Přidejte následující `ListFiles` metoda.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Tento kód nejdřív vymaže **ListBox**.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> Metoda pak načte kolekci řetězce, jednu pro každý soubor v adresáři. `GetFiles` Metoda přijímá argumentem vzor hledání se budou načítat soubory, které odpovídají konkrétním vzorku. V tomto příkladu jsou vráceny jen soubory s příponou .txt.  
  
     Řetězce, které se vrátí pomocí `GetFiles` metoda se pak přidají do **ListBox**.  
  
4.  Spusťte aplikaci. Klikněte **Procházet** tlačítko. V **vyhledat složku** dialogové okno, přejděte do složky, která obsahuje soubory s příponou .txt, a potom vyberte složku a klikněte na tlačítko **OK**.  
  
     `ListBox` Obsahuje seznam soubory s příponou .txt ve vybrané složce.  
  
5.  Zastavte spuštěné aplikace.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Získání atributů souboru a obsahu z textového souboru  
  
1.  Vytvoření `Click` obslužné rutiny události pro `examineButton` poklepáním na ovládací prvek na formuláři.  
  
2.  Přidejte následující kód, který `Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     Kód ověřuje, že je položka vybrána v `ListBox`. Poté získá položka z cesty k souboru `ListBox`. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> Metoda se používá k ověření, zda soubor stále existuje.  
  
     Cesta k souboru je odeslán jako argument k `GetTextForOutput` metoda, která se přidá v dalším kroku. Tato metoda vrátí řetězec, který obsahuje informace o souboru. Informace o souboru se zobrazí v **MessageBox**.  
  
3.  Přidejte následující `GetTextForOutput` metoda.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     Kód používá <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> metoda získat soubor parametrů. Soubor parametrů jsou přidány do <xref:System.Text.StringBuilder>.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> Metoda přečte obsah souboru do <xref:System.IO.StreamReader>. První řádek obsahu se získávají z `StreamReader` a přidají se do `StringBuilder`.  
  
4.  Spusťte aplikaci. Klikněte na tlačítko **Procházet**a přejděte do složky, která obsahuje soubory s příponou .txt. Click **OK**.  
  
     Vyberte soubor v `ListBox`a potom klikněte na **vyhledejte**. A `MessageBox` zobrazuje informace o souboru.  
  
5.  Zastavte spuštěné aplikace.  
  
### <a name="to-add-a-log-entry"></a>Chcete-li přidat položky protokolu  
  
1.  Přidejte následující kód do konce `examineButton_Click` obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     Kód nastaví cesta k souboru protokolu pro umístění souboru protokolu ve stejném adresáři jako u vybraného souboru. Text položky protokolu nastavena na aktuální datum a čas, za nímž následuje informací o souboru.  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody s `append` argument nastaven na hodnotu `True`, se používá k vytvoření položky protokolu.  
  
2.  Spusťte aplikaci. Přejděte do textového souboru, vyberte ho v `ListBox`, vyberte **uložit výsledky** zaškrtněte políčko a potom klikněte na **vyhledejte**. Ověřte, že je na zapisovat položky protokolu `log.txt` souboru.  
  
3.  Zastavte spuštěné aplikace.  
  
### <a name="to-use-the-current-directory"></a>Chcete-li používat aktuální adresář  
  
1.  Vytvoření obslužné rutiny události pro `Form1_Load` poklepáním na formulář.  
  
2.  Přidejte následující kód do obslužné rutiny události.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Tento kód nastaví výchozí adresář prohlížeče složky k aktuálnímu adresáři.  
  
3.  Spusťte aplikaci. Když kliknete na tlačítko **Procházet** první **vyhledat složku** otevře se dialogové okno k aktuálnímu adresáři.  
  
4.  Zastavte spuštěné aplikace.  
  
### <a name="to-selectively-enable-controls"></a>Povolit některé ovládací prvky  
  
1.  Přidejte následující `SetEnabled` metoda.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` Metoda povolí nebo zakáže ovládací prvky v závislosti na tom, jestli je položka vybrána v `ListBox`.  
  
2.  Vytvoření `SelectedIndexChanged` obslužné rutiny události pro `filesListBox` dvojitým kliknutím `ListBox` ovládací prvek na formuláři.  
  
3.  Přidejte volání `SetEnabled` v novém `filesListBox_SelectedIndexChanged` obslužné rutiny události.  
  
4.  Přidejte volání `SetEnabled` na konci `browseButton_Click` obslužné rutiny události.  
  
5.  Přidejte volání `SetEnabled` na konci `Form1_Load` obslužné rutiny události.  
  
6.  Spusťte aplikaci. **Uložit výsledky** zaškrtávací políčko a **vyhledejte** tlačítko jsou zakázané, pokud není vybrána položka v `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Úplný příklad pomocí My.Computer.FileSystem  
 Toto je kompletní příklad.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>Úplný příklad pomocí System.IO  
 Následující příklad ekvivalentní používá třídy z <xref:System.IO> obor názvů místo použití `My.Computer.FileSystem` objekty.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [Návod: Práce se soubory pomocí metod rozhraní .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

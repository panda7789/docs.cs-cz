---
title: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed363efeeef008927f2c34b393de66ca4ccbb0bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)
Tento návod ukazuje, jak otevřít a přečíst si souboru pomocí <xref:System.IO.StreamReader> třídy, zkontrolujte, pokud je soubor přistupuje, hledat řetězec v souboru pro čtení s instancí <xref:System.IO.StreamReader> třídy a zapisovat do souboru pomocí <xref:System.IO.StreamWriter> třídy.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Vytvoření aplikace  
 Spuštění sady Visual Studio a projekt začněte vytvořením formulář, který uživatel může použít k zápisu do určeného soubor.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Na **soubor** nabídce vyberte možnost **nový projekt**.  
  
2.  V **nový projekt** podokně klikněte na tlačítko **aplikace Windows**.  
  
3.  V **název** zadejte `MyDiary` a klikněte na tlačítko **OK**.  
  
     Visual Studio. přidá projekt **Průzkumníku řešení**a **Návrhář formulářů Windows** otevře.  
  
4.  Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.  
  
|**Objekt**|**Vlastnosti**|**Hodnota**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Submit`<br /><br /> **Odeslat záznam**|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Clear`<br /><br /> **Zrušte zaškrtnutí položky**|  
|<xref:System.Windows.Forms.TextBox>|**Jméno**<br /><br /> **Text**<br /><br /> **Víceřádkového výrazu**|`Entry`<br /><br /> **Zadejte prosím něco.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Při zápisu do souboru  
 Chcete-li přidat možnost zapisovat do souboru pomocí aplikace, použijte <xref:System.IO.StreamWriter> třídy. <xref:System.IO.StreamWriter> je určený pro výstup znaků v určitém kódování, zatímco <xref:System.IO.Stream> třída je určená pro bajtový vstup a výstup. Použití <xref:System.IO.StreamWriter> pro zapsání řádků informací do standardního textového souboru. Další informace o <xref:System.IO.StreamWriter> třídy najdete v tématu <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Chcete-li přidat funkce zápisu  
  
1.  Z **zobrazení** nabídce zvolte **kód** otevření editoru kódu.  
  
2.  Protože aplikace odkazuje <xref:System.IO> obor názvů, přidejte následující příkazy od samého začátku kódu, před deklaraci třídy pro daný formulář, který začíná `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Před zápisu do souboru, je nutné vytvořit instanci <xref:System.IO.StreamWriter> třídy.  
  
3.  Z **zobrazení** nabídce zvolte **Návrhář** se vrátíte do **Návrhář formulářů Windows**. Dvakrát klikněte `Submit` tlačítko vytvořte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro tlačítko a poté přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  Prostředí Visual Studio integrované vývoj prostředí (IDE) se vrátit do editoru kódu a umístěte kurzor do obslužné rutiny události, kde měli byste přidat kód.  
  
1.  K zápisu do souboru, použijte <xref:System.IO.StreamWriter.Write%2A> metodu <xref:System.IO.StreamWriter> třídy. Následující kód přidejte přímo po `Dim fw As StreamWriter`. Nemusíte si dělat starosti, bude vyvolána výjimka pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Ujistěte se, že uživatel nemůže odeslat prázdná položka přidáním následujícího kódu přímo po `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Protože se jedná soukromý, uživatel bude chcete přiřadit datum pro každou položku. Vložte následující kód po `fw = New StreamWriter("C:\MyDiary.txt", True)` nastavit proměnnou `Today` na aktuální datum.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Nakonec připojit kód zrušit zaškrtnutí <xref:System.Windows.Forms.TextBox>. Přidejte následující kód, který `Clear` tlačítka <xref:System.Windows.Forms.Control.Click> událostí.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>Přidání funkcí zobrazení do deníku  
 V této části přidáte funkci, která zobrazí poslední položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Můžete také přidat <xref:System.Windows.Forms.ComboBox> , zobrazí různé položky a ze kterého může uživatel vybrat položku zobrazíte v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Instance <xref:System.IO.StreamReader> třídy čtení z `MyDiary.txt`. Podobně jako <xref:System.IO.StreamWriter> třídy <xref:System.IO.StreamReader> je určen pro použití s textovými soubory.  
  
 Pro tento oddíl návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte příslušné hodnoty pro jejich vlastnosti.  
  
|Ovládací prvek|Vlastnosti|Hodnoty|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Jméno**<br /><br /> **Viditelné**<br /><br /> **Velikost**<br /><br /> **Víceřádkového výrazu**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Display`<br /><br /> **Zobrazení**|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`GetEntries`<br /><br /> **Získání položek**|  
|<xref:System.Windows.Forms.ComboBox>|**Jméno**<br /><br /> **Text**<br /><br /> **povoleno**|`PickEntries`<br /><br /> **Vyberte položku**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>K vyplnění pole se seznamem  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> Slouží k zobrazení dat, které uživatel odeslal položku, tak si uživatel může vybrat položku z konkrétního data. Vytvoření <xref:System.Windows.Forms.Control.Click> obslužná rutina události `GetEntries` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  K testování kódu, stisknutím klávesy F5 zkompilování aplikace a pak klikněte na tlačítko **najít položky**. Klikněte na šipku rozevíracího seznamu ve <xref:System.Windows.Forms.ComboBox> k zobrazení vstupní data.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Vybrat a zobrazit jednotlivé položky  
  
1.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `Display` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  K testování kódu, stisknutím klávesy F5 kompilace aplikace a pak odeslat záznam. Klikněte na tlačítko **najít položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox>a potom klikněte na **zobrazení**. Zobrazí obsah vybrané položky v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Povolení uživatelům odstranit nebo upravit položky  
 Nakonec můžete zahrnout další funkce umožňuje uživatelům odstranit nebo upravit položky pomocí `DeleteEntry` a `EditEntry` tlačítka. Obě tlačítka zůstanou neaktivní, pokud se zobrazí položka.  
  
 Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.  
  
|Ovládací prvek|Vlastnosti|Hodnoty|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **povoleno**|`DeleteEntry`<br /><br /> **Odstranit položku**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **povoleno**|`EditEntry`<br /><br /> **Upravit položku**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **povoleno**|`SubmitEdit`<br /><br /> **Odeslání úpravy**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Chcete-li povolit odstranění a úpravy položek  
  
1.  Přidejte následující kód, který `Display` tlačítka <xref:System.Windows.Forms.Control.Click> událostí, po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `DeleteEntry` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Jakmile uživatel zobrazí položku, `EditEntry` aktivuje tlačítko. Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> události `Display` tlačítko po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `EditEntry` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `SubmitEdit` tlačítko a přidejte následující kód  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 K testování kódu, stisknutím klávesy F5 kompilace aplikace. Klikněte na tlačítko **najít položky**, vyberte položku a pak klikněte na tlačítko **zobrazení**. Položka se zobrazí v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Klikněte na tlačítko **upravte položku**. Položka se zobrazí v `Entry` <xref:System.Windows.Forms.TextBox>. Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na tlačítko **odeslání upravit**. Otevřete `MyDiary.txt` souboru k ověření vašich oprav. Nyní vyberte položku a klikněte na tlačítko **odstranit položku**. Když <xref:System.Windows.Forms.MessageBox> požádá o potvrzení, klikněte na tlačítko **OK**. Zavřete aplikaci a otevřete `MyDiary.txt` potvrďte odstranění.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [Návody](../../../../visual-basic/walkthroughs.md)

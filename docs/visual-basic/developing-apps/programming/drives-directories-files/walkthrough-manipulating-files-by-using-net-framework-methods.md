---
title: Manipulace se soubory pomocí metod .NET Framework (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: fc02b795834dba4a777dc78f4c8179238ac593af
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582481"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)

Tento názorný postup ukazuje, jak otevřít a číst soubor pomocí třídy <xref:System.IO.StreamReader>, zkontrolujte, zda je k souboru přístup, vyhledejte řetězec v souboru, který je čten s instancí třídy <xref:System.IO.StreamReader> a zapište do souboru pomocí třídy <xref:System.IO.StreamWriter>.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Vytvoření aplikace

Spusťte aplikaci Visual Studio a spusťte projekt vytvořením formuláře, který uživatel může použít k zápisu do určeného souboru.

### <a name="to-create-the-project"></a>Vytvoření projektu

1. V nabídce **soubor** vyberte **Nový projekt**.

2. V podokně **Nový projekt** klikněte na položku **aplikace systému Windows**.

3. Do pole **název** zadejte `MyDiary` a klikněte na **OK**.

     Visual Studio přidá projekt do **Průzkumník řešení**a otevře se **Návrhář formulářů** .

4. Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.

|**Předmětů**|**Vlastnosti**|**Hodnota**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Submit`<br /><br /> **Odeslat položku**|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Clear`<br /><br /> **Vymazat položku**|
|<xref:System.Windows.Forms.TextBox>|**Jméno**<br /><br /> **Text**<br /><br /> **Víceřádkový**|`Entry`<br /><br /> **Zadejte prosím něco.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zápis do souboru

Chcete-li přidat možnost zapisovat do souboru přes aplikaci, použijte třídu <xref:System.IO.StreamWriter>. <xref:System.IO.StreamWriter> je navržen pro výstup znaku v konkrétním kódování, zatímco <xref:System.IO.Stream> třída je navržena pro bajtový vstup a výstup. Pro zápis řádků informací do standardního textového souboru použijte <xref:System.IO.StreamWriter>. Další informace o třídě <xref:System.IO.StreamWriter> naleznete v tématu <xref:System.IO.StreamWriter>.

### <a name="to-add-writing-functionality"></a>Přidání funkce zápisu

1. V nabídce **zobrazení** vyberte **kód** a otevřete Editor kódu.

2. Vzhledem k tomu, že aplikace odkazuje na obor názvů <xref:System.IO>, přidejte následující příkazy na začátek kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1`.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Před zápisem do souboru je nutné vytvořit instanci třídy <xref:System.IO.StreamWriter>.

3. V nabídce **zobrazení** vyberte možnost **Návrhář** a vraťte se k **Návrhář formulářů**. Dvojím kliknutím na tlačítko `Submit` vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko a poté přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Integrované vývojové prostředí (IDE) sady Visual Studio se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli kód přidat.

1. Chcete-li zapisovat do souboru, použijte metodu <xref:System.IO.StreamWriter.Write%2A> třídy <xref:System.IO.StreamWriter>. Následující kód přidejte přímo po `Dim fw As StreamWriter`. Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Ujistěte se, že uživatel nemůže odeslat prázdnou položku přidáním následujícího kódu přímo po `Dim ReadString As String`.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Vzhledem k tomu, že se jedná o Diary, bude uživatel chtít přiřadit datum ke každé položce. Po `fw = New StreamWriter("C:\MyDiary.txt", True)` vložte následující kód, který nastaví proměnnou `Today` na aktuální datum.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Nakonec připojte kód pro vymazání <xref:System.Windows.Forms.TextBox>. Do události <xref:System.Windows.Forms.Control.Click> tlačítka `Clear` přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Přidání funkcí zobrazení do Diary

V této části přidáte funkci, která zobrazí nejnovější položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Můžete také přidat <xref:System.Windows.Forms.ComboBox>, který zobrazuje různé položky a ze kterého může uživatel vybrat položku, která se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Instance třídy <xref:System.IO.StreamReader> čte z `MyDiary.txt`. Podobně jako třída <xref:System.IO.StreamWriter> je <xref:System.IO.StreamReader> určena pro použití s textovými soubory.

Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty jejich vlastností.

|Control|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Jméno**<br /><br /> **Zobrazeny**<br /><br /> **Hodnota**<br /><br /> **Víceřádkový**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`Display`<br /><br /> **Otevřete**|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**|`GetEntries`<br /><br /> **Získat položky**|
|<xref:System.Windows.Forms.ComboBox>|**Jméno**<br /><br /> **Text**<br /><br /> **Umožněn**|`PickEntries`<br /><br /> **Vybrat položku**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Naplnění pole se seznamem

1. @No__t_1 `PickEntries` slouží k zobrazení dat, na kterých uživatel každou položku odesílá, takže uživatel může vybrat položku z konkrétní datum. Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> k tlačítku `GetEntries` a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak klikněte na tlačítko **získat položky**. Kliknutím na šipku rozevíracího seznamu v <xref:System.Windows.Forms.ComboBox> zobrazíte data položky.

### <a name="to-choose-and-display-individual-entries"></a>Výběr a zobrazení jednotlivých položek

1. Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `Display` a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak odešlete položku. Klikněte na **získat položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox> a pak klikněte na **Zobrazit**. Obsah vybrané položky se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`.

## <a name="enabling-users-to-delete-or-modify-entries"></a>Povolení uživatelům odstraňovat nebo upravovat položky

Nakonec můžete zahrnout další funkce, které umožní uživatelům odstranit nebo upravit položku pomocí `DeleteEntry` a `EditEntry`ch tlačítek. Obě tlačítka zůstanou zakázaná, pokud není zobrazená položka.

Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.

|Control|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **Umožněn**|`DeleteEntry`<br /><br /> **Odstranit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **Umožněn**|`EditEntry`<br /><br /> **Upravit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Jméno**<br /><br /> **Text**<br /><br /> **Umožněn**|`SubmitEdit`<br /><br /> **Odeslat úpravu**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Povolení odstranění a změny položek

1. Po `DisplayEntry.Text = ReadString` přidejte následující kód do události <xref:System.Windows.Forms.Control.Click> tlačítka `Display`.

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `DeleteEntry` a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Když uživatel zobrazí položku, bude tlačítko `EditEntry` aktivní. Po `DisplayEntry.Text = ReadString` přidejte následující kód k události <xref:System.Windows.Forms.Control.Click> `Display` tlačítka.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `EditEntry` a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `SubmitEdit` a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace. Klikněte na **získat položky**, vyberte položku a pak klikněte na **Zobrazit**. Položka se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Klikněte na **Upravit položku**. Položka se zobrazí v <xref:System.Windows.Forms.TextBox> `Entry`. Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na **Odeslat úpravu**. Otevřete soubor `MyDiary.txt` a potvrďte tak opravu. Nyní vyberte položku a klikněte na položku **Odstranit položku**. Po potvrzení žádosti <xref:System.Windows.Forms.MessageBox> klikněte na tlačítko **OK**. Zavřete aplikaci a otevřete `MyDiary.txt` potvrďte odstranění.

## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Návody](../../../../visual-basic/walkthroughs.md)

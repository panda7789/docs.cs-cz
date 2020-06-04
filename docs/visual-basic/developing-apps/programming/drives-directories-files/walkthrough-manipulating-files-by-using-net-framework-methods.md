---
title: Práce se soubory pomocí metod rozhraní .NET Framework
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
ms.openlocfilehash: 9abb87f3f6cdefefef29eb37c2c2d4d15155e93d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406648"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)

Tento názorný postup ukazuje, jak otevřít a číst soubor pomocí <xref:System.IO.StreamReader> třídy, zjistit, zda je k souboru přístup, vyhledejte řetězec v souboru, který je čten s instancí <xref:System.IO.StreamReader> třídy, a zapište do souboru pomocí <xref:System.IO.StreamWriter> třídy.

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
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Submit`<br /><br /> **Odeslat položku**|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Clear`<br /><br /> **Vymazat položku**|
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Text**<br /><br /> **Multiline**|`Entry`<br /><br /> **Zadejte prosím něco.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zápis do souboru

Chcete-li přidat možnost zapisovat do souboru přes aplikaci, použijte <xref:System.IO.StreamWriter> třídu. <xref:System.IO.StreamWriter>je navržen pro výstup znaku v konkrétním kódování, zatímco <xref:System.IO.Stream> Třída je navržena pro bajtový vstup a výstup. Používá <xref:System.IO.StreamWriter> se pro zápis řádků informací do standardního textového souboru. Další informace o <xref:System.IO.StreamWriter> třídě naleznete v tématu <xref:System.IO.StreamWriter> .

### <a name="to-add-writing-functionality"></a>Přidání funkce zápisu

1. V nabídce **zobrazení** vyberte **kód** a otevřete Editor kódu.

2. Vzhledem k tomu, že aplikace odkazuje na <xref:System.IO> obor názvů, přidejte následující příkazy na začátek kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1` .

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Před zápisem do souboru je nutné vytvořit instanci <xref:System.IO.StreamWriter> třídy.

3. V nabídce **zobrazení** vyberte možnost **Návrhář** a vraťte se k **Návrhář formulářů**. Dvakrát klikněte na `Submit` tlačítko a vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro tlačítko a poté přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Integrované vývojové prostředí (IDE) sady Visual Studio se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli kód přidat.

1. Chcete-li zapisovat do souboru, použijte <xref:System.IO.StreamWriter.Write%2A> metodu <xref:System.IO.StreamWriter> třídy. Následující kód přidejte přímo za `Dim fw As StreamWriter` . Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Ujistěte se, že uživatel nemůže odeslat prázdnou položku přidáním následujícího kódu přímo za `Dim ReadString As String` .

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Vzhledem k tomu, že se jedná o Diary, bude uživatel chtít přiřadit datum ke každé položce. Po `fw = New StreamWriter("C:\MyDiary.txt", True)` nastavení proměnné na aktuální datum vložte následující kód `Today` .

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Nakonec připojte kód pro vymazání <xref:System.Windows.Forms.TextBox> . Přidejte následující kód do `Clear` <xref:System.Windows.Forms.Control.Click> události tlačítka.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Přidání funkcí zobrazení do Diary

V této části přidáte funkci, která zobrazí nejnovější položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox> . Můžete také přidat a zobrazit <xref:System.Windows.Forms.ComboBox> různé položky, ze kterých může uživatel vybrat položku, která se zobrazí v `DisplayEntry` <xref:System.Windows.Forms.TextBox> . Instance <xref:System.IO.StreamReader> třídy načtená z `MyDiary.txt` . Podobně jako <xref:System.IO.StreamWriter> Třída <xref:System.IO.StreamReader> je určena pro použití s textovými soubory.

Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty jejich vlastností.

|Řízení|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Visible**<br /><br /> **Velikost**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Display`<br /><br /> **Displej**|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`GetEntries`<br /><br /> **Získat položky**|
|<xref:System.Windows.Forms.ComboBox>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`PickEntries`<br /><br /> **Vybrat položku**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Naplnění pole se seznamem

1. `PickEntries` <xref:System.Windows.Forms.ComboBox> Slouží k zobrazení dat, kdy uživatel každou položku odešle, takže uživatel může vybrat položku z konkrétní datum. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro `GetEntries` tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak klikněte na tlačítko **získat položky**. Kliknutím na šipku rozevíracího seznamu v části <xref:System.Windows.Forms.ComboBox> zobrazíte data položky.

### <a name="to-choose-and-display-individual-entries"></a>Výběr a zobrazení jednotlivých položek

1. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro `Display` tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak odešlete položku. Klikněte na **získat položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox> a pak klikněte na **Zobrazit**. Obsah vybrané položky se zobrazí v části `DisplayEntry` <xref:System.Windows.Forms.TextBox> .

## <a name="enabling-users-to-delete-or-modify-entries"></a>Povolení uživatelům odstraňovat nebo upravovat položky

Nakonec můžete zahrnout další funkce, které uživatelům umožňují odstranit nebo upravit položku pomocí `DeleteEntry` `EditEntry` tlačítek a. Obě tlačítka zůstanou zakázaná, pokud není zobrazená položka.

Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.

|Řízení|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`DeleteEntry`<br /><br /> **Odstranit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`EditEntry`<br /><br /> **Upravit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`SubmitEdit`<br /><br /> **Odeslat úpravu**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Povolení odstranění a změny položek

1. Přidejte následující kód do `Display` <xref:System.Windows.Forms.Control.Click> události tlačítka, poté `DisplayEntry.Text = ReadString` .

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro `DeleteEntry` tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Když uživatel zobrazí položku, `EditEntry` tlačítko se aktivuje. Přidejte následující kód pro <xref:System.Windows.Forms.Control.Click> událost `Display` tlačítka po `DisplayEntry.Text = ReadString` .

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro `EditEntry` tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro `SubmitEdit` tlačítko a přidejte následující kód

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace. Klikněte na **získat položky**, vyberte položku a pak klikněte na **Zobrazit**. Položka se zobrazí v části `DisplayEntry` <xref:System.Windows.Forms.TextBox> . Klikněte na **Upravit položku**. Položka se zobrazí v části `Entry` <xref:System.Windows.Forms.TextBox> . Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na **Odeslat úpravu**. Otevřete `MyDiary.txt` soubor a potvrďte jeho opravu. Nyní vyberte položku a klikněte na položku **Odstranit položku**. Po <xref:System.Windows.Forms.MessageBox> potvrzení požadavků klikněte na tlačítko **OK**. Zavřete aplikaci a otevřete `MyDiary.txt` ji a potvrďte odstranění.

## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Postupy](../../../walkthroughs.md)

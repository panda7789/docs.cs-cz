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
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333786"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)

Tento návod ukazuje, jak otevřít a číst <xref:System.IO.StreamReader> soubor pomocí třídy, zkontrolujte, zda je soubor přístupný, vyhledejte řetězec <xref:System.IO.StreamReader> v souboru přečteném <xref:System.IO.StreamWriter> s instancí třídy a zapište do souboru pomocí třídy.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Vytvoření aplikace

Spusťte visual studio a začněte projekt vytvořením formuláře, který může uživatel použít k zápisu do určeného souboru.

### <a name="to-create-the-project"></a>Vytvoření projektu

1. V nabídce **Soubor** vyberte **Nový projekt**.

2. V podokně **Nový projekt** klepněte na **položku Aplikace systému Windows**.

3. V **Name** poli Název `MyDiary` zadejte a klepněte na **tlačítko OK**.

     Visual Studio přidá projekt do **Průzkumníka řešení**a otevře se **Návrhář formulářů systému Windows.**

4. Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.

|**Objekt**|**Vlastnosti**|**Hodnotu**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Submit`<br /><br /> **Odeslat položku**|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Clear`<br /><br /> **Vymazat vstup**|
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Text**<br /><br /> **Multiline**|`Entry`<br /><br /> **Zadejte něco.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Zápis do souboru

Chcete-li přidat možnost zápisu do souboru <xref:System.IO.StreamWriter> prostřednictvím aplikace, použijte třídu. <xref:System.IO.StreamWriter>je určen pro znakový výstup v určitém <xref:System.IO.Stream> kódování, zatímco třída je určena pro vstup a výstup bajtů. Používá <xref:System.IO.StreamWriter> se pro zápis řádků informací do standardního textového souboru. Další informace o <xref:System.IO.StreamWriter> třídě <xref:System.IO.StreamWriter>naleznete v tématu .

### <a name="to-add-writing-functionality"></a>Přidání funkce zápisu

1. V nabídce **Zobrazení** zvolte **Kód,** chcete-li otevřít Editor kódu.

2. Vzhledem k tomu, že aplikace odkazuje na obor <xref:System.IO> názvů, přidejte následující příkazy na samém začátku kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1`.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Před zápisem do souboru je nutné <xref:System.IO.StreamWriter> vytvořit instanci třídy.

3. Z nabídky **Zobrazení** zvolte **Návrhář,** abyste se vrátili do **Návrháře formulářů systému Windows**. Poklepáním `Submit` na tlačítko <xref:System.Windows.Forms.Control.Click> vytvořte obslužnou rutinu události pro tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Integrované vývojové prostředí sady Visual Studio (IDE) se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli přidat kód.

1. Chcete-li zapisovat <xref:System.IO.StreamWriter.Write%2A> do <xref:System.IO.StreamWriter> souboru, použijte metodu třídy. Přidejte následující kód `Dim fw As StreamWriter`přímo za . Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor není nalezen, protože bude vytvořen, pokud již neexistuje.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. Ujistěte se, že uživatel nemůže odeslat prázdnou `Dim ReadString As String`položku přidáním následujícího kódu přímo za .

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Vzhledem k tomu, že se jedná o deník, uživatel bude chtít přiřadit datum každé položce. Chcete-li nastavit `fw = New StreamWriter("C:\MyDiary.txt", True)` proměnnou `Today` na aktuální datum, vložte následující kód.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Nakonec připojte kód k <xref:System.Windows.Forms.TextBox>vymazání . Přidejte následující kód `Clear` k <xref:System.Windows.Forms.Control.Click> události tlačítka.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Přidání funkcí zobrazení do deníku

V této části přidáte funkci, která zobrazuje `DisplayEntry` <xref:System.Windows.Forms.TextBox>nejnovější položku v . Můžete také přidat <xref:System.Windows.Forms.ComboBox> položku, která zobrazuje různé položky a ze `DisplayEntry` <xref:System.Windows.Forms.TextBox>které může uživatel vybrat položku, která se má zobrazit v rozhraní . Instance třídy <xref:System.IO.StreamReader> čte `MyDiary.txt`z . Stejně <xref:System.IO.StreamWriter> jako <xref:System.IO.StreamReader> třída, je určen pro použití s textovými soubory.

Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.

|Řízení|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Visible**<br /><br /> **Velikost**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Display`<br /><br /> **Displej**|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`GetEntries`<br /><br /> **Získat položky**|
|<xref:System.Windows.Forms.ComboBox>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`PickEntries`<br /><br /> **Výběr položky**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Naplnění pole se seznamem

1. Slouží `PickEntries` <xref:System.Windows.Forms.ComboBox> k zobrazení dat, kdy uživatel odešle každou položku, takže uživatel může vybrat položku z určitého data. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události na `GetEntries` tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Chcete-li kód otestovat, zkompilujte aplikaci stisknutím klávesy F5 a klepněte na tlačítko **Získat položky**. Kliknutím na šipku rozevíracího seznamu v rozevírací šišce <xref:System.Windows.Forms.ComboBox> zobrazíte data zadání.

### <a name="to-choose-and-display-individual-entries"></a>Výběr a zobrazení jednotlivých položek

1. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `Display` události pro tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Chcete-li kód otestovat, zkompilujte přihlášku stisknutím klávesy F5 a odešlete položku. Klepněte na tlačítko Získat <xref:System.Windows.Forms.ComboBox> **položky**, vyberte položku z položky a potom klepněte na tlačítko **Zobrazit**. Obsah vybrané položky se `DisplayEntry` <xref:System.Windows.Forms.TextBox>zobrazí v .

## <a name="enabling-users-to-delete-or-modify-entries"></a>Povolení uživatelům k odstranění nebo úpravě položek

Nakonec můžete zahrnout další funkce umožňuje uživatelům odstranit nebo `DeleteEntry` upravit `EditEntry` položku pomocí a tlačítka. Obě tlačítka zůstávají zakázána, pokud není zobrazena položka.

Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.

|Řízení|Vlastnosti|Hodnoty|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`DeleteEntry`<br /><br /> **Odstranit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`EditEntry`<br /><br /> **Upravit položku**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Enabled** (Povoleno)|`SubmitEdit`<br /><br /> **Odeslat upravit**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Povolení mazání a úprav položek

1. Přidejte následující kód `Display` k <xref:System.Windows.Forms.Control.Click> události tlačítka `DisplayEntry.Text = ReadString`po .

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `DeleteEntry` události pro tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Když uživatel zobrazí položku, `EditEntry` tlačítko se aktivuje. Přidejte následující kód <xref:System.Windows.Forms.Control.Click> k `Display` události `DisplayEntry.Text = ReadString`tlačítka po .

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `EditEntry` události pro tlačítko a přidejte následující kód.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny `SubmitEdit` události pro tlačítko a přidání následujícího kódu

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Chcete-li kód otestovat, zkompilujte aplikaci stisknutím klávesy F5. Klikněte na **Získat položky**, vyberte položku a potom klikněte na **Zobrazit**. Položka se zobrazí `DisplayEntry` <xref:System.Windows.Forms.TextBox>v . Klepněte na **tlačítko Upravit položku**. Položka se zobrazí `Entry` <xref:System.Windows.Forms.TextBox>v . Upravte položku `Entry` <xref:System.Windows.Forms.TextBox> v souboru a klepněte na **tlačítko Odeslat upravit**. Otevřete `MyDiary.txt` soubor a potvrďte opravu. Nyní vyberte položku a klepněte na **tlačítko Odstranit položku**. Po <xref:System.Windows.Forms.MessageBox> potvrzení požadavků klepněte na tlačítko **OK**. Zavřete aplikaci `MyDiary.txt` a otevřete pro potvrzení odstranění.

## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Názorné postupy](../../../../visual-basic/walkthroughs.md)

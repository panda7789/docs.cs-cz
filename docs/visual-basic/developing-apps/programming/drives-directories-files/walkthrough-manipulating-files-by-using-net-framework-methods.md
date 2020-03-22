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
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="3d483-102">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d483-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="3d483-103">Tento návod ukazuje, jak otevřít a číst <xref:System.IO.StreamReader> soubor pomocí třídy, zkontrolujte, zda je soubor přístupný, vyhledejte řetězec <xref:System.IO.StreamReader> v souboru přečteném <xref:System.IO.StreamWriter> s instancí třídy a zapište do souboru pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="3d483-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="3d483-104">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="3d483-104">Creating the Application</span></span>

<span data-ttu-id="3d483-105">Spusťte visual studio a začněte projekt vytvořením formuláře, který může uživatel použít k zápisu do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="3d483-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="3d483-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="3d483-106">To create the project</span></span>

1. <span data-ttu-id="3d483-107">V nabídce **Soubor** vyberte **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="3d483-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="3d483-108">V podokně **Nový projekt** klepněte na **položku Aplikace systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="3d483-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="3d483-109">V **Name** poli Název `MyDiary` zadejte a klepněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="3d483-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="3d483-110">Visual Studio přidá projekt do **Průzkumníka řešení**a otevře se **Návrhář formulářů systému Windows.**</span><span class="sxs-lookup"><span data-stu-id="3d483-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="3d483-111">Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d483-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3d483-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="3d483-112">**Object**</span></span>|<span data-ttu-id="3d483-113">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="3d483-113">**Properties**</span></span>|<span data-ttu-id="3d483-114">**Hodnotu**</span><span class="sxs-lookup"><span data-stu-id="3d483-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-115">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-115">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="3d483-117">**Odeslat položku**</span><span class="sxs-lookup"><span data-stu-id="3d483-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-118">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-118">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="3d483-120">**Vymazat vstup**</span><span class="sxs-lookup"><span data-stu-id="3d483-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="3d483-121">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-121">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-122">**Text**</span></span><br /><br /> <span data-ttu-id="3d483-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="3d483-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="3d483-124">**Zadejte něco.**</span><span class="sxs-lookup"><span data-stu-id="3d483-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="3d483-125">Zápis do souboru</span><span class="sxs-lookup"><span data-stu-id="3d483-125">Writing to the File</span></span>

<span data-ttu-id="3d483-126">Chcete-li přidat možnost zápisu do souboru <xref:System.IO.StreamWriter> prostřednictvím aplikace, použijte třídu.</span><span class="sxs-lookup"><span data-stu-id="3d483-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="3d483-127"><xref:System.IO.StreamWriter>je určen pro znakový výstup v určitém <xref:System.IO.Stream> kódování, zatímco třída je určena pro vstup a výstup bajtů.</span><span class="sxs-lookup"><span data-stu-id="3d483-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="3d483-128">Používá <xref:System.IO.StreamWriter> se pro zápis řádků informací do standardního textového souboru.</span><span class="sxs-lookup"><span data-stu-id="3d483-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="3d483-129">Další informace o <xref:System.IO.StreamWriter> třídě <xref:System.IO.StreamWriter>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="3d483-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="3d483-130">Přidání funkce zápisu</span><span class="sxs-lookup"><span data-stu-id="3d483-130">To add writing functionality</span></span>

1. <span data-ttu-id="3d483-131">V nabídce **Zobrazení** zvolte **Kód,** chcete-li otevřít Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="3d483-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="3d483-132">Vzhledem k tomu, že aplikace odkazuje na obor <xref:System.IO> názvů, přidejte následující příkazy na samém začátku kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="3d483-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="3d483-133">Před zápisem do souboru je nutné <xref:System.IO.StreamWriter> vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="3d483-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="3d483-134">Z nabídky **Zobrazení** zvolte **Návrhář,** abyste se vrátili do **Návrháře formulářů systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="3d483-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="3d483-135">Poklepáním `Submit` na tlačítko <xref:System.Windows.Forms.Control.Click> vytvořte obslužnou rutinu události pro tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="3d483-136">Integrované vývojové prostředí sady Visual Studio (IDE) se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli přidat kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="3d483-137">Chcete-li zapisovat <xref:System.IO.StreamWriter.Write%2A> do <xref:System.IO.StreamWriter> souboru, použijte metodu třídy.</span><span class="sxs-lookup"><span data-stu-id="3d483-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="3d483-138">Přidejte následující kód `Dim fw As StreamWriter`přímo za .</span><span class="sxs-lookup"><span data-stu-id="3d483-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="3d483-139">Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor není nalezen, protože bude vytvořen, pokud již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="3d483-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="3d483-140">Ujistěte se, že uživatel nemůže odeslat prázdnou `Dim ReadString As String`položku přidáním následujícího kódu přímo za .</span><span class="sxs-lookup"><span data-stu-id="3d483-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="3d483-141">Vzhledem k tomu, že se jedná o deník, uživatel bude chtít přiřadit datum každé položce.</span><span class="sxs-lookup"><span data-stu-id="3d483-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="3d483-142">Chcete-li nastavit `fw = New StreamWriter("C:\MyDiary.txt", True)` proměnnou `Today` na aktuální datum, vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="3d483-143">Nakonec připojte kód k <xref:System.Windows.Forms.TextBox>vymazání .</span><span class="sxs-lookup"><span data-stu-id="3d483-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3d483-144">Přidejte následující kód `Clear` k <xref:System.Windows.Forms.Control.Click> události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="3d483-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="3d483-145">Přidání funkcí zobrazení do deníku</span><span class="sxs-lookup"><span data-stu-id="3d483-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="3d483-146">V této části přidáte funkci, která zobrazuje `DisplayEntry` <xref:System.Windows.Forms.TextBox>nejnovější položku v .</span><span class="sxs-lookup"><span data-stu-id="3d483-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3d483-147">Můžete také přidat <xref:System.Windows.Forms.ComboBox> položku, která zobrazuje různé položky a ze `DisplayEntry` <xref:System.Windows.Forms.TextBox>které může uživatel vybrat položku, která se má zobrazit v rozhraní .</span><span class="sxs-lookup"><span data-stu-id="3d483-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3d483-148">Instance třídy <xref:System.IO.StreamReader> čte `MyDiary.txt`z .</span><span class="sxs-lookup"><span data-stu-id="3d483-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="3d483-149">Stejně <xref:System.IO.StreamWriter> jako <xref:System.IO.StreamReader> třída, je určen pro použití s textovými soubory.</span><span class="sxs-lookup"><span data-stu-id="3d483-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="3d483-150">Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d483-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3d483-151">Řízení</span><span class="sxs-lookup"><span data-stu-id="3d483-151">Control</span></span>|<span data-ttu-id="3d483-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3d483-152">Properties</span></span>|<span data-ttu-id="3d483-153">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="3d483-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="3d483-154">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-154">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-155">**Visible**</span><span class="sxs-lookup"><span data-stu-id="3d483-155">**Visible**</span></span><br /><br /> <span data-ttu-id="3d483-156">**Velikost**</span><span class="sxs-lookup"><span data-stu-id="3d483-156">**Size**</span></span><br /><br /> <span data-ttu-id="3d483-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="3d483-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-158">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-158">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="3d483-160">**Displej**</span><span class="sxs-lookup"><span data-stu-id="3d483-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-161">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-161">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-162">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="3d483-163">**Získat položky**</span><span class="sxs-lookup"><span data-stu-id="3d483-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="3d483-164">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-164">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-165">**Text**</span></span><br /><br /> <span data-ttu-id="3d483-166">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="3d483-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="3d483-167">**Výběr položky**</span><span class="sxs-lookup"><span data-stu-id="3d483-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="3d483-168">Naplnění pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="3d483-168">To populate the combo box</span></span>

1. <span data-ttu-id="3d483-169">Slouží `PickEntries` <xref:System.Windows.Forms.ComboBox> k zobrazení dat, kdy uživatel odešle každou položku, takže uživatel může vybrat položku z určitého data.</span><span class="sxs-lookup"><span data-stu-id="3d483-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="3d483-170">Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události na `GetEntries` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="3d483-171">Chcete-li kód otestovat, zkompilujte aplikaci stisknutím klávesy F5 a klepněte na tlačítko **Získat položky**.</span><span class="sxs-lookup"><span data-stu-id="3d483-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="3d483-172">Kliknutím na šipku rozevíracího seznamu v rozevírací šišce <xref:System.Windows.Forms.ComboBox> zobrazíte data zadání.</span><span class="sxs-lookup"><span data-stu-id="3d483-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="3d483-173">Výběr a zobrazení jednotlivých položek</span><span class="sxs-lookup"><span data-stu-id="3d483-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="3d483-174">Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `Display` události pro tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="3d483-175">Chcete-li kód otestovat, zkompilujte přihlášku stisknutím klávesy F5 a odešlete položku.</span><span class="sxs-lookup"><span data-stu-id="3d483-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="3d483-176">Klepněte na tlačítko Získat <xref:System.Windows.Forms.ComboBox> **položky**, vyberte položku z položky a potom klepněte na tlačítko **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="3d483-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="3d483-177">Obsah vybrané položky se `DisplayEntry` <xref:System.Windows.Forms.TextBox>zobrazí v .</span><span class="sxs-lookup"><span data-stu-id="3d483-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="3d483-178">Povolení uživatelům k odstranění nebo úpravě položek</span><span class="sxs-lookup"><span data-stu-id="3d483-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="3d483-179">Nakonec můžete zahrnout další funkce umožňuje uživatelům odstranit nebo `DeleteEntry` upravit `EditEntry` položku pomocí a tlačítka.</span><span class="sxs-lookup"><span data-stu-id="3d483-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="3d483-180">Obě tlačítka zůstávají zakázána, pokud není zobrazena položka.</span><span class="sxs-lookup"><span data-stu-id="3d483-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="3d483-181">Přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3d483-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="3d483-182">Řízení</span><span class="sxs-lookup"><span data-stu-id="3d483-182">Control</span></span>|<span data-ttu-id="3d483-183">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3d483-183">Properties</span></span>|<span data-ttu-id="3d483-184">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="3d483-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-185">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-185">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-186">**Text**</span></span><br /><br /> <span data-ttu-id="3d483-187">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="3d483-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="3d483-188">**Odstranit položku**</span><span class="sxs-lookup"><span data-stu-id="3d483-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-189">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-189">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-190">**Text**</span></span><br /><br /> <span data-ttu-id="3d483-191">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="3d483-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="3d483-192">**Upravit položku**</span><span class="sxs-lookup"><span data-stu-id="3d483-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="3d483-193">**Název**</span><span class="sxs-lookup"><span data-stu-id="3d483-193">**Name**</span></span><br /><br /> <span data-ttu-id="3d483-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="3d483-194">**Text**</span></span><br /><br /> <span data-ttu-id="3d483-195">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="3d483-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="3d483-196">**Odeslat upravit**</span><span class="sxs-lookup"><span data-stu-id="3d483-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="3d483-197">Povolení mazání a úprav položek</span><span class="sxs-lookup"><span data-stu-id="3d483-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="3d483-198">Přidejte následující kód `Display` k <xref:System.Windows.Forms.Control.Click> události tlačítka `DisplayEntry.Text = ReadString`po .</span><span class="sxs-lookup"><span data-stu-id="3d483-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="3d483-199">Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `DeleteEntry` události pro tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="3d483-200">Když uživatel zobrazí položku, `EditEntry` tlačítko se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="3d483-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="3d483-201">Přidejte následující kód <xref:System.Windows.Forms.Control.Click> k `Display` události `DisplayEntry.Text = ReadString`tlačítka po .</span><span class="sxs-lookup"><span data-stu-id="3d483-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="3d483-202">Vytvořte <xref:System.Windows.Forms.Control.Click> obslužnou rutinu `EditEntry` události pro tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="3d483-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="3d483-203">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny `SubmitEdit` události pro tlačítko a přidání následujícího kódu</span><span class="sxs-lookup"><span data-stu-id="3d483-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="3d483-204">Chcete-li kód otestovat, zkompilujte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="3d483-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="3d483-205">Klikněte na **Získat položky**, vyberte položku a potom klikněte na **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="3d483-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="3d483-206">Položka se zobrazí `DisplayEntry` <xref:System.Windows.Forms.TextBox>v .</span><span class="sxs-lookup"><span data-stu-id="3d483-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3d483-207">Klepněte na **tlačítko Upravit položku**.</span><span class="sxs-lookup"><span data-stu-id="3d483-207">Click **Edit Entry**.</span></span> <span data-ttu-id="3d483-208">Položka se zobrazí `Entry` <xref:System.Windows.Forms.TextBox>v .</span><span class="sxs-lookup"><span data-stu-id="3d483-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="3d483-209">Upravte položku `Entry` <xref:System.Windows.Forms.TextBox> v souboru a klepněte na **tlačítko Odeslat upravit**.</span><span class="sxs-lookup"><span data-stu-id="3d483-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="3d483-210">Otevřete `MyDiary.txt` soubor a potvrďte opravu.</span><span class="sxs-lookup"><span data-stu-id="3d483-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="3d483-211">Nyní vyberte položku a klepněte na **tlačítko Odstranit položku**.</span><span class="sxs-lookup"><span data-stu-id="3d483-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="3d483-212">Po <xref:System.Windows.Forms.MessageBox> potvrzení požadavků klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="3d483-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="3d483-213">Zavřete aplikaci `MyDiary.txt` a otevřete pro potvrzení odstranění.</span><span class="sxs-lookup"><span data-stu-id="3d483-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d483-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d483-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="3d483-215">Názorné postupy</span><span class="sxs-lookup"><span data-stu-id="3d483-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)

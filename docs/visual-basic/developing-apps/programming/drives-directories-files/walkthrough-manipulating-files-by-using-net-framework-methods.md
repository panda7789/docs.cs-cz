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
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="8b932-102">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b932-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="8b932-103">Tento názorný postup ukazuje, jak otevřít a číst soubor pomocí <xref:System.IO.StreamReader> třídy, zjistit, zda je k souboru přístup, vyhledejte řetězec v souboru, který je čten s instancí <xref:System.IO.StreamReader> třídy, a zapište do souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b932-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="8b932-104">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="8b932-104">Creating the Application</span></span>

<span data-ttu-id="8b932-105">Spusťte aplikaci Visual Studio a spusťte projekt vytvořením formuláře, který uživatel může použít k zápisu do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="8b932-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="8b932-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="8b932-106">To create the project</span></span>

1. <span data-ttu-id="8b932-107">V nabídce **soubor** vyberte **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="8b932-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="8b932-108">V podokně **Nový projekt** klikněte na položku **aplikace systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="8b932-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="8b932-109">Do pole **název** zadejte `MyDiary` a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b932-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="8b932-110">Visual Studio přidá projekt do **Průzkumník řešení**a otevře se **Návrhář formulářů** .</span><span class="sxs-lookup"><span data-stu-id="8b932-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="8b932-111">Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="8b932-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="8b932-112">**Předmětů**</span><span class="sxs-lookup"><span data-stu-id="8b932-112">**Object**</span></span>|<span data-ttu-id="8b932-113">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="8b932-113">**Properties**</span></span>|<span data-ttu-id="8b932-114">**Osa**</span><span class="sxs-lookup"><span data-stu-id="8b932-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-115">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-115">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="8b932-117">**Odeslat položku**</span><span class="sxs-lookup"><span data-stu-id="8b932-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-118">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-118">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="8b932-120">**Vymazat položku**</span><span class="sxs-lookup"><span data-stu-id="8b932-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="8b932-121">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-121">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-122">**Text**</span></span><br /><br /> <span data-ttu-id="8b932-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="8b932-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="8b932-124">**Zadejte prosím něco.**</span><span class="sxs-lookup"><span data-stu-id="8b932-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="8b932-125">Zápis do souboru</span><span class="sxs-lookup"><span data-stu-id="8b932-125">Writing to the File</span></span>

<span data-ttu-id="8b932-126">Chcete-li přidat možnost zapisovat do souboru přes aplikaci, použijte <xref:System.IO.StreamWriter> třídu.</span><span class="sxs-lookup"><span data-stu-id="8b932-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="8b932-127"><xref:System.IO.StreamWriter>je navržen pro výstup znaku v konkrétním kódování, zatímco <xref:System.IO.Stream> třída je navržena pro bajtový vstup a výstup.</span><span class="sxs-lookup"><span data-stu-id="8b932-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="8b932-128">Používá <xref:System.IO.StreamWriter> se pro zápis řádků informací do standardního textového souboru.</span><span class="sxs-lookup"><span data-stu-id="8b932-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="8b932-129">Další informace o <xref:System.IO.StreamWriter> třídě naleznete v tématu <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="8b932-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="8b932-130">Přidání funkce zápisu</span><span class="sxs-lookup"><span data-stu-id="8b932-130">To add writing functionality</span></span>

1. <span data-ttu-id="8b932-131">V nabídce **zobrazení** vyberte **kód** a otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="8b932-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="8b932-132">Vzhledem k tomu, že <xref:System.IO> aplikace odkazuje na obor názvů, přidejte následující příkazy na začátek kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="8b932-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="8b932-133">Před zápisem do souboru je nutné vytvořit instanci <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b932-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="8b932-134">V nabídce **zobrazení** vyberte možnost **Návrhář** a vraťte se k **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="8b932-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="8b932-135">Dvakrát klikněte na `Submit` tlačítko a vytvořte obslužnou rutinu <xref:System.Windows.Forms.Control.Click> události pro tlačítko a poté přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="8b932-136">Integrované vývojové prostředí (IDE) sady Visual Studio se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli kód přidat.</span><span class="sxs-lookup"><span data-stu-id="8b932-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="8b932-137">Chcete-li zapisovat do souboru, použijte <xref:System.IO.StreamWriter.Write%2A> metodu <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b932-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="8b932-138">Následující kód přidejte přímo za `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="8b932-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="8b932-139">Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="8b932-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="8b932-140">Ujistěte se, že uživatel nemůže odeslat prázdnou položku přidáním následujícího kódu přímo za `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="8b932-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="8b932-141">Vzhledem k tomu, že se jedná o Diary, bude uživatel chtít přiřadit datum ke každé položce.</span><span class="sxs-lookup"><span data-stu-id="8b932-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="8b932-142">Po `fw = New StreamWriter("C:\MyDiary.txt", True)` nastavení proměnné `Today` na aktuální datum vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="8b932-143">Nakonec připojte kód pro vymazání <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8b932-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="8b932-144">Přidejte následující kód do `Clear` <xref:System.Windows.Forms.Control.Click> události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="8b932-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="8b932-145">Přidání funkcí zobrazení do Diary</span><span class="sxs-lookup"><span data-stu-id="8b932-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="8b932-146">V této části přidáte funkci, která zobrazí nejnovější položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8b932-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="8b932-147">Můžete také přidat a <xref:System.Windows.Forms.ComboBox> zobrazit různé položky, ze kterých může uživatel vybrat položku, která se zobrazí v. `DisplayEntry` <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="8b932-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="8b932-148">Instance <xref:System.IO.StreamReader> třídy načtená z `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="8b932-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="8b932-149">Podobně jako <xref:System.IO.StreamWriter> třída <xref:System.IO.StreamReader> je určena pro použití s textovými soubory.</span><span class="sxs-lookup"><span data-stu-id="8b932-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="8b932-150">Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="8b932-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="8b932-151">Řízení</span><span class="sxs-lookup"><span data-stu-id="8b932-151">Control</span></span>|<span data-ttu-id="8b932-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8b932-152">Properties</span></span>|<span data-ttu-id="8b932-153">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="8b932-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="8b932-154">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-154">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-155">**Visible**</span><span class="sxs-lookup"><span data-stu-id="8b932-155">**Visible**</span></span><br /><br /> <span data-ttu-id="8b932-156">**Velikost**</span><span class="sxs-lookup"><span data-stu-id="8b932-156">**Size**</span></span><br /><br /> <span data-ttu-id="8b932-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="8b932-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-158">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-158">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="8b932-160">**Displej**</span><span class="sxs-lookup"><span data-stu-id="8b932-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-161">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-161">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-162">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="8b932-163">**Získat položky**</span><span class="sxs-lookup"><span data-stu-id="8b932-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="8b932-164">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-164">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-165">**Text**</span></span><br /><br /> <span data-ttu-id="8b932-166">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="8b932-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="8b932-167">**Vybrat položku**</span><span class="sxs-lookup"><span data-stu-id="8b932-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="8b932-168">Naplnění pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="8b932-168">To populate the combo box</span></span>

1. <span data-ttu-id="8b932-169">`PickEntries` Slouží k zobrazení dat, kdy uživatel každou položku odešle, takže uživatel může vybrat položku z konkrétní <xref:System.Windows.Forms.ComboBox> datum.</span><span class="sxs-lookup"><span data-stu-id="8b932-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="8b932-170">Vytvořte obslužnou <xref:System.Windows.Forms.Control.Click> rutinu události pro `GetEntries` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="8b932-171">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak klikněte na tlačítko **získat položky**.</span><span class="sxs-lookup"><span data-stu-id="8b932-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="8b932-172">Kliknutím na šipku rozevíracího seznamu v části <xref:System.Windows.Forms.ComboBox> zobrazíte data položky.</span><span class="sxs-lookup"><span data-stu-id="8b932-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="8b932-173">Výběr a zobrazení jednotlivých položek</span><span class="sxs-lookup"><span data-stu-id="8b932-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="8b932-174">Vytvořte obslužnou <xref:System.Windows.Forms.Control.Click> rutinu události pro `Display` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="8b932-175">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak odešlete položku.</span><span class="sxs-lookup"><span data-stu-id="8b932-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="8b932-176">Klikněte na **získat položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox>a pak klikněte na **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="8b932-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="8b932-177">Obsah vybrané položky se zobrazí v části `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8b932-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="8b932-178">Povolení uživatelům odstraňovat nebo upravovat položky</span><span class="sxs-lookup"><span data-stu-id="8b932-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="8b932-179">Nakonec můžete zahrnout další funkce, které uživatelům umožňují odstranit nebo upravit položku pomocí `DeleteEntry` tlačítek a. `EditEntry`</span><span class="sxs-lookup"><span data-stu-id="8b932-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="8b932-180">Obě tlačítka zůstanou zakázaná, pokud není zobrazená položka.</span><span class="sxs-lookup"><span data-stu-id="8b932-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="8b932-181">Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="8b932-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="8b932-182">Řízení</span><span class="sxs-lookup"><span data-stu-id="8b932-182">Control</span></span>|<span data-ttu-id="8b932-183">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8b932-183">Properties</span></span>|<span data-ttu-id="8b932-184">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="8b932-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-185">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-185">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-186">**Text**</span></span><br /><br /> <span data-ttu-id="8b932-187">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="8b932-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="8b932-188">**Odstranit položku**</span><span class="sxs-lookup"><span data-stu-id="8b932-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-189">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-189">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-190">**Text**</span></span><br /><br /> <span data-ttu-id="8b932-191">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="8b932-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="8b932-192">**Upravit položku**</span><span class="sxs-lookup"><span data-stu-id="8b932-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="8b932-193">**Název**</span><span class="sxs-lookup"><span data-stu-id="8b932-193">**Name**</span></span><br /><br /> <span data-ttu-id="8b932-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="8b932-194">**Text**</span></span><br /><br /> <span data-ttu-id="8b932-195">**Enabled** (Povoleno)</span><span class="sxs-lookup"><span data-stu-id="8b932-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="8b932-196">**Odeslat úpravu**</span><span class="sxs-lookup"><span data-stu-id="8b932-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="8b932-197">Povolení odstranění a změny položek</span><span class="sxs-lookup"><span data-stu-id="8b932-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="8b932-198">Přidejte následující kód do `Display` <xref:System.Windows.Forms.Control.Click> události tlačítka, poté. `DisplayEntry.Text = ReadString`</span><span class="sxs-lookup"><span data-stu-id="8b932-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="8b932-199">Vytvořte obslužnou <xref:System.Windows.Forms.Control.Click> rutinu události pro `DeleteEntry` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="8b932-200">Když uživatel zobrazí položku, `EditEntry` tlačítko se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="8b932-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="8b932-201">Přidejte následující kód pro <xref:System.Windows.Forms.Control.Click> událost `Display` tlačítka po. `DisplayEntry.Text = ReadString`</span><span class="sxs-lookup"><span data-stu-id="8b932-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="8b932-202">Vytvořte obslužnou <xref:System.Windows.Forms.Control.Click> rutinu události pro `EditEntry` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8b932-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="8b932-203">Vytvořte obslužnou <xref:System.Windows.Forms.Control.Click> rutinu události pro `SubmitEdit` tlačítko a přidejte následující kód</span><span class="sxs-lookup"><span data-stu-id="8b932-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="8b932-204">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b932-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="8b932-205">Klikněte na **získat položky**, vyberte položku a pak klikněte na **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="8b932-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="8b932-206">Položka se zobrazí v části `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8b932-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="8b932-207">Klikněte na **Upravit položku**.</span><span class="sxs-lookup"><span data-stu-id="8b932-207">Click **Edit Entry**.</span></span> <span data-ttu-id="8b932-208">Položka se zobrazí v části `Entry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8b932-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="8b932-209">Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na **Odeslat úpravu**.</span><span class="sxs-lookup"><span data-stu-id="8b932-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="8b932-210">Otevřete `MyDiary.txt` soubor a potvrďte jeho opravu.</span><span class="sxs-lookup"><span data-stu-id="8b932-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="8b932-211">Nyní vyberte položku a klikněte na položku **Odstranit položku**.</span><span class="sxs-lookup"><span data-stu-id="8b932-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="8b932-212">Po potvrzení <xref:System.Windows.Forms.MessageBox> požadavků klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b932-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="8b932-213">Zavřete aplikaci a otevřete `MyDiary.txt` ji a potvrďte odstranění.</span><span class="sxs-lookup"><span data-stu-id="8b932-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b932-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b932-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="8b932-215">Postupy</span><span class="sxs-lookup"><span data-stu-id="8b932-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)

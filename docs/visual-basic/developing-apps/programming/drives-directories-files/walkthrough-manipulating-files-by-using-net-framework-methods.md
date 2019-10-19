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
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="e157e-102">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e157e-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="e157e-103">Tento názorný postup ukazuje, jak otevřít a číst soubor pomocí třídy <xref:System.IO.StreamReader>, zkontrolujte, zda je k souboru přístup, vyhledejte řetězec v souboru, který je čten s instancí třídy <xref:System.IO.StreamReader> a zapište do souboru pomocí třídy <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="e157e-104">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="e157e-104">Creating the Application</span></span>

<span data-ttu-id="e157e-105">Spusťte aplikaci Visual Studio a spusťte projekt vytvořením formuláře, který uživatel může použít k zápisu do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="e157e-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="e157e-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="e157e-106">To create the project</span></span>

1. <span data-ttu-id="e157e-107">V nabídce **soubor** vyberte **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e157e-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="e157e-108">V podokně **Nový projekt** klikněte na položku **aplikace systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="e157e-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="e157e-109">Do pole **název** zadejte `MyDiary` a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e157e-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="e157e-110">Visual Studio přidá projekt do **Průzkumník řešení**a otevře se **Návrhář formulářů** .</span><span class="sxs-lookup"><span data-stu-id="e157e-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="e157e-111">Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="e157e-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="e157e-112">**Předmětů**</span><span class="sxs-lookup"><span data-stu-id="e157e-112">**Object**</span></span>|<span data-ttu-id="e157e-113">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="e157e-113">**Properties**</span></span>|<span data-ttu-id="e157e-114">**Hodnota**</span><span class="sxs-lookup"><span data-stu-id="e157e-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-115">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="e157e-117">**Odeslat položku**</span><span class="sxs-lookup"><span data-stu-id="e157e-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-118">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-118">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="e157e-120">**Vymazat položku**</span><span class="sxs-lookup"><span data-stu-id="e157e-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="e157e-121">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-121">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-122">**Text**</span></span><br /><br /> <span data-ttu-id="e157e-123">**Víceřádkový**</span><span class="sxs-lookup"><span data-stu-id="e157e-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="e157e-124">**Zadejte prosím něco.**</span><span class="sxs-lookup"><span data-stu-id="e157e-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="e157e-125">Zápis do souboru</span><span class="sxs-lookup"><span data-stu-id="e157e-125">Writing to the File</span></span>

<span data-ttu-id="e157e-126">Chcete-li přidat možnost zapisovat do souboru přes aplikaci, použijte třídu <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="e157e-127"><xref:System.IO.StreamWriter> je navržen pro výstup znaku v konkrétním kódování, zatímco <xref:System.IO.Stream> třída je navržena pro bajtový vstup a výstup.</span><span class="sxs-lookup"><span data-stu-id="e157e-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="e157e-128">Pro zápis řádků informací do standardního textového souboru použijte <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="e157e-129">Další informace o třídě <xref:System.IO.StreamWriter> naleznete v tématu <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="e157e-130">Přidání funkce zápisu</span><span class="sxs-lookup"><span data-stu-id="e157e-130">To add writing functionality</span></span>

1. <span data-ttu-id="e157e-131">V nabídce **zobrazení** vyberte **kód** a otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="e157e-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="e157e-132">Vzhledem k tomu, že aplikace odkazuje na obor názvů <xref:System.IO>, přidejte následující příkazy na začátek kódu před deklaraci třídy pro formulář, který začíná `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="e157e-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="e157e-133">Před zápisem do souboru je nutné vytvořit instanci třídy <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="e157e-134">V nabídce **zobrazení** vyberte možnost **Návrhář** a vraťte se k **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="e157e-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="e157e-135">Dvojím kliknutím na tlačítko `Submit` vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko a poté přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="e157e-136">Integrované vývojové prostředí (IDE) sady Visual Studio se vrátí do editoru kódu a umístí kurzor do obslužné rutiny události, kde byste měli kód přidat.</span><span class="sxs-lookup"><span data-stu-id="e157e-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="e157e-137">Chcete-li zapisovat do souboru, použijte metodu <xref:System.IO.StreamWriter.Write%2A> třídy <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="e157e-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="e157e-138">Následující kód přidejte přímo po `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="e157e-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="e157e-139">Nemusíte se obávat, že výjimka bude vyvolána, pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e157e-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="e157e-140">Ujistěte se, že uživatel nemůže odeslat prázdnou položku přidáním následujícího kódu přímo po `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="e157e-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="e157e-141">Vzhledem k tomu, že se jedná o Diary, bude uživatel chtít přiřadit datum ke každé položce.</span><span class="sxs-lookup"><span data-stu-id="e157e-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="e157e-142">Po `fw = New StreamWriter("C:\MyDiary.txt", True)` vložte následující kód, který nastaví proměnnou `Today` na aktuální datum.</span><span class="sxs-lookup"><span data-stu-id="e157e-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="e157e-143">Nakonec připojte kód pro vymazání <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e157e-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e157e-144">Do události <xref:System.Windows.Forms.Control.Click> tlačítka `Clear` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="e157e-145">Přidání funkcí zobrazení do Diary</span><span class="sxs-lookup"><span data-stu-id="e157e-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="e157e-146">V této části přidáte funkci, která zobrazí nejnovější položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e157e-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e157e-147">Můžete také přidat <xref:System.Windows.Forms.ComboBox>, který zobrazuje různé položky a ze kterého může uživatel vybrat položku, která se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`.</span><span class="sxs-lookup"><span data-stu-id="e157e-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e157e-148">Instance třídy <xref:System.IO.StreamReader> čte z `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="e157e-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="e157e-149">Podobně jako třída <xref:System.IO.StreamWriter> je <xref:System.IO.StreamReader> určena pro použití s textovými soubory.</span><span class="sxs-lookup"><span data-stu-id="e157e-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="e157e-150">Pro tuto část návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="e157e-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="e157e-151">Control</span><span class="sxs-lookup"><span data-stu-id="e157e-151">Control</span></span>|<span data-ttu-id="e157e-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e157e-152">Properties</span></span>|<span data-ttu-id="e157e-153">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e157e-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="e157e-154">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-154">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-155">**Zobrazeny**</span><span class="sxs-lookup"><span data-stu-id="e157e-155">**Visible**</span></span><br /><br /> <span data-ttu-id="e157e-156">**Hodnota**</span><span class="sxs-lookup"><span data-stu-id="e157e-156">**Size**</span></span><br /><br /> <span data-ttu-id="e157e-157">**Víceřádkový**</span><span class="sxs-lookup"><span data-stu-id="e157e-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-158">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-158">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="e157e-160">**Otevřete**</span><span class="sxs-lookup"><span data-stu-id="e157e-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-161">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-161">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-162">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="e157e-163">**Získat položky**</span><span class="sxs-lookup"><span data-stu-id="e157e-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="e157e-164">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-164">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-165">**Text**</span></span><br /><br /> <span data-ttu-id="e157e-166">**Umožněn**</span><span class="sxs-lookup"><span data-stu-id="e157e-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="e157e-167">**Vybrat položku**</span><span class="sxs-lookup"><span data-stu-id="e157e-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="e157e-168">Naplnění pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="e157e-168">To populate the combo box</span></span>

1. <span data-ttu-id="e157e-169">@No__t_1 `PickEntries` slouží k zobrazení dat, na kterých uživatel každou položku odesílá, takže uživatel může vybrat položku z konkrétní datum.</span><span class="sxs-lookup"><span data-stu-id="e157e-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="e157e-170">Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> k tlačítku `GetEntries` a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="e157e-171">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak klikněte na tlačítko **získat položky**.</span><span class="sxs-lookup"><span data-stu-id="e157e-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="e157e-172">Kliknutím na šipku rozevíracího seznamu v <xref:System.Windows.Forms.ComboBox> zobrazíte data položky.</span><span class="sxs-lookup"><span data-stu-id="e157e-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="e157e-173">Výběr a zobrazení jednotlivých položek</span><span class="sxs-lookup"><span data-stu-id="e157e-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="e157e-174">Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `Display` a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="e157e-175">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace a pak odešlete položku.</span><span class="sxs-lookup"><span data-stu-id="e157e-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="e157e-176">Klikněte na **získat položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox> a pak klikněte na **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="e157e-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="e157e-177">Obsah vybrané položky se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`.</span><span class="sxs-lookup"><span data-stu-id="e157e-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="e157e-178">Povolení uživatelům odstraňovat nebo upravovat položky</span><span class="sxs-lookup"><span data-stu-id="e157e-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="e157e-179">Nakonec můžete zahrnout další funkce, které umožní uživatelům odstranit nebo upravit položku pomocí `DeleteEntry` a `EditEntry`ch tlačítek.</span><span class="sxs-lookup"><span data-stu-id="e157e-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="e157e-180">Obě tlačítka zůstanou zakázaná, pokud není zobrazená položka.</span><span class="sxs-lookup"><span data-stu-id="e157e-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="e157e-181">Do formuláře přidejte ovládací prvky v následující tabulce a nastavte odpovídající hodnoty jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="e157e-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="e157e-182">Control</span><span class="sxs-lookup"><span data-stu-id="e157e-182">Control</span></span>|<span data-ttu-id="e157e-183">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e157e-183">Properties</span></span>|<span data-ttu-id="e157e-184">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="e157e-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-185">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-185">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-186">**Text**</span></span><br /><br /> <span data-ttu-id="e157e-187">**Umožněn**</span><span class="sxs-lookup"><span data-stu-id="e157e-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="e157e-188">**Odstranit položku**</span><span class="sxs-lookup"><span data-stu-id="e157e-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-189">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-189">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-190">**Text**</span></span><br /><br /> <span data-ttu-id="e157e-191">**Umožněn**</span><span class="sxs-lookup"><span data-stu-id="e157e-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="e157e-192">**Upravit položku**</span><span class="sxs-lookup"><span data-stu-id="e157e-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="e157e-193">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e157e-193">**Name**</span></span><br /><br /> <span data-ttu-id="e157e-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="e157e-194">**Text**</span></span><br /><br /> <span data-ttu-id="e157e-195">**Umožněn**</span><span class="sxs-lookup"><span data-stu-id="e157e-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="e157e-196">**Odeslat úpravu**</span><span class="sxs-lookup"><span data-stu-id="e157e-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="e157e-197">Povolení odstranění a změny položek</span><span class="sxs-lookup"><span data-stu-id="e157e-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="e157e-198">Po `DisplayEntry.Text = ReadString` přidejte následující kód do události <xref:System.Windows.Forms.Control.Click> tlačítka `Display`.</span><span class="sxs-lookup"><span data-stu-id="e157e-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="e157e-199">Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `DeleteEntry` a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="e157e-200">Když uživatel zobrazí položku, bude tlačítko `EditEntry` aktivní.</span><span class="sxs-lookup"><span data-stu-id="e157e-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="e157e-201">Po `DisplayEntry.Text = ReadString` přidejte následující kód k události <xref:System.Windows.Forms.Control.Click> `Display` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e157e-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="e157e-202">Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `EditEntry` a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="e157e-203">Vytvořte obslužnou rutinu události <xref:System.Windows.Forms.Control.Click> pro tlačítko `SubmitEdit` a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e157e-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="e157e-204">Chcete-li otestovat kód, stiskněte klávesu F5 pro zkompilování aplikace.</span><span class="sxs-lookup"><span data-stu-id="e157e-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="e157e-205">Klikněte na **získat položky**, vyberte položku a pak klikněte na **Zobrazit**.</span><span class="sxs-lookup"><span data-stu-id="e157e-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="e157e-206">Položka se zobrazí v <xref:System.Windows.Forms.TextBox> `DisplayEntry`.</span><span class="sxs-lookup"><span data-stu-id="e157e-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e157e-207">Klikněte na **Upravit položku**.</span><span class="sxs-lookup"><span data-stu-id="e157e-207">Click **Edit Entry**.</span></span> <span data-ttu-id="e157e-208">Položka se zobrazí v <xref:System.Windows.Forms.TextBox> `Entry`.</span><span class="sxs-lookup"><span data-stu-id="e157e-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e157e-209">Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na **Odeslat úpravu**.</span><span class="sxs-lookup"><span data-stu-id="e157e-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="e157e-210">Otevřete soubor `MyDiary.txt` a potvrďte tak opravu.</span><span class="sxs-lookup"><span data-stu-id="e157e-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="e157e-211">Nyní vyberte položku a klikněte na položku **Odstranit položku**.</span><span class="sxs-lookup"><span data-stu-id="e157e-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="e157e-212">Po potvrzení žádosti <xref:System.Windows.Forms.MessageBox> klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e157e-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="e157e-213">Zavřete aplikaci a otevřete `MyDiary.txt` potvrďte odstranění.</span><span class="sxs-lookup"><span data-stu-id="e157e-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="e157e-214">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e157e-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="e157e-215">Návody</span><span class="sxs-lookup"><span data-stu-id="e157e-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)

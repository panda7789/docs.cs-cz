---
title: "Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc42dee640271ef84d35ceeb039d98741d296c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="cf12e-102">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf12e-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="cf12e-103">Tento návod ukazuje, jak otevřít a přečíst si souboru pomocí <xref:System.IO.StreamReader> třídy, zkontrolujte, pokud je soubor přistupuje, hledat řetězec v souboru pro čtení s instancí <xref:System.IO.StreamReader> třídy a zapisovat do souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf12e-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="cf12e-104">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="cf12e-104">Creating the Application</span></span>  
 <span data-ttu-id="cf12e-105">Spustit [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] a projekt začněte vytvořením formulář, který uživatel může použít k zápisu do určeného souboru.</span><span class="sxs-lookup"><span data-stu-id="cf12e-105">Start [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="cf12e-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="cf12e-106">To create the project</span></span>  
  
1.  <span data-ttu-id="cf12e-107">Na **soubor** nabídce vyberte možnost **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="cf12e-108">V **nový projekt** podokně klikněte na tlačítko **aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="cf12e-109">V **název** zadejte `MyDiary` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="cf12e-110">přidá projekt **Průzkumníku řešení**a **Návrhář formulářů Windows** otevře.</span><span class="sxs-lookup"><span data-stu-id="cf12e-110"> adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="cf12e-111">Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf12e-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="cf12e-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="cf12e-112">**Object**</span></span>|<span data-ttu-id="cf12e-113">**Vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="cf12e-113">**Properties**</span></span>|<span data-ttu-id="cf12e-114">**Hodnota**</span><span class="sxs-lookup"><span data-stu-id="cf12e-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-115">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="cf12e-117">**Odeslat záznam**</span><span class="sxs-lookup"><span data-stu-id="cf12e-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-118">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-118">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="cf12e-120">**Zrušte zaškrtnutí položky**</span><span class="sxs-lookup"><span data-stu-id="cf12e-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="cf12e-121">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-121">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-122">**Text**</span></span><br /><br /> <span data-ttu-id="cf12e-123">**Víceřádkového výrazu**</span><span class="sxs-lookup"><span data-stu-id="cf12e-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="cf12e-124">**Zadejte prosím něco.**</span><span class="sxs-lookup"><span data-stu-id="cf12e-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="cf12e-125">Při zápisu do souboru</span><span class="sxs-lookup"><span data-stu-id="cf12e-125">Writing to the File</span></span>  
 <span data-ttu-id="cf12e-126">Chcete-li přidat možnost zapisovat do souboru pomocí aplikace, použijte <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf12e-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="cf12e-127"><xref:System.IO.StreamWriter>je určený pro výstup znaků v určitém kódování, zatímco <xref:System.IO.Stream> třída je určená pro bajtový vstup a výstup.</span><span class="sxs-lookup"><span data-stu-id="cf12e-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="cf12e-128">Použití <xref:System.IO.StreamWriter> pro zapsání řádků informací do standardního textového souboru.</span><span class="sxs-lookup"><span data-stu-id="cf12e-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="cf12e-129">Další informace o <xref:System.IO.StreamWriter> třídy najdete v tématu <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="cf12e-130">Chcete-li přidat funkce zápisu</span><span class="sxs-lookup"><span data-stu-id="cf12e-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="cf12e-131">Z **zobrazení** nabídce zvolte **kód** otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="cf12e-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="cf12e-132">Protože aplikace odkazuje <xref:System.IO> obor názvů, přidejte následující příkazy od samého začátku kódu, před deklaraci třídy pro daný formulář, který začíná `Public Class Form1`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     <span data-ttu-id="cf12e-133">Před zápisu do souboru, je nutné vytvořit instanci <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf12e-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="cf12e-134">Z **zobrazení** nabídce zvolte **Návrhář** se vrátíte do **Návrhář formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="cf12e-135">Dvakrát klikněte `Submit` tlačítko vytvořte <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro tlačítko a poté přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="cf12e-136">Prostředí Visual Studio integrované vývoj prostředí (IDE) se vrátit do editoru kódu a umístěte kurzor do obslužné rutiny události, kde měli byste přidat kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="cf12e-137">K zápisu do souboru, použijte <xref:System.IO.StreamWriter.Write%2A> metodu <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf12e-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="cf12e-138">Následující kód přidejte přímo po `Dim fw As StreamWriter`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="cf12e-139">Nemusíte si dělat starosti, bude vyvolána výjimka pokud soubor nebyl nalezen, protože bude vytvořen, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="cf12e-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  <span data-ttu-id="cf12e-140">Ujistěte se, že uživatel nemůže odeslat prázdná položka přidáním následujícího kódu přímo po `Dim ReadString As String`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  <span data-ttu-id="cf12e-141">Protože se jedná soukromý, uživatel bude chcete přiřadit datum pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="cf12e-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="cf12e-142">Vložte následující kód po `fw = New StreamWriter("C:\MyDiary.txt", True)` nastavit proměnnou `Today` na aktuální datum.</span><span class="sxs-lookup"><span data-stu-id="cf12e-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  <span data-ttu-id="cf12e-143">Nakonec připojit kód zrušit zaškrtnutí <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="cf12e-144">Přidejte následující kód, který `Clear` tlačítka <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="cf12e-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="cf12e-145">Přidání funkcí zobrazení do deníku</span><span class="sxs-lookup"><span data-stu-id="cf12e-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="cf12e-146">V této části přidáte funkci, která zobrazí poslední položku v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="cf12e-147">Můžete také přidat <xref:System.Windows.Forms.ComboBox> , zobrazí různé položky a ze kterého může uživatel vybrat položku zobrazíte v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="cf12e-148">Instance <xref:System.IO.StreamReader> třídy čtení z `MyDiary.txt`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="cf12e-149">Podobně jako <xref:System.IO.StreamWriter> třídy <xref:System.IO.StreamReader> je určen pro použití s textovými soubory.</span><span class="sxs-lookup"><span data-stu-id="cf12e-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="cf12e-150">Pro tento oddíl návodu přidejte ovládací prvky v následující tabulce do formuláře a nastavte příslušné hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf12e-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="cf12e-151">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="cf12e-151">Control</span></span>|<span data-ttu-id="cf12e-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cf12e-152">Properties</span></span>|<span data-ttu-id="cf12e-153">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="cf12e-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="cf12e-154">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-154">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-155">**Viditelné**</span><span class="sxs-lookup"><span data-stu-id="cf12e-155">**Visible**</span></span><br /><br /> <span data-ttu-id="cf12e-156">**Velikost**</span><span class="sxs-lookup"><span data-stu-id="cf12e-156">**Size**</span></span><br /><br /> <span data-ttu-id="cf12e-157">**Víceřádkového výrazu**</span><span class="sxs-lookup"><span data-stu-id="cf12e-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-158">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-158">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="cf12e-160">**Zobrazení**</span><span class="sxs-lookup"><span data-stu-id="cf12e-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-161">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-161">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-162">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="cf12e-163">**Získání položek**</span><span class="sxs-lookup"><span data-stu-id="cf12e-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="cf12e-164">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-164">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-165">**Text**</span></span><br /><br /> <span data-ttu-id="cf12e-166">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="cf12e-167">**Vyberte položku**</span><span class="sxs-lookup"><span data-stu-id="cf12e-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="cf12e-168">K vyplnění pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="cf12e-168">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="cf12e-169">`PickEntries` <xref:System.Windows.Forms.ComboBox> Slouží k zobrazení dat, které uživatel odeslal položku, tak si uživatel může vybrat položku z konkrétního data.</span><span class="sxs-lookup"><span data-stu-id="cf12e-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="cf12e-170">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužná rutina události `GetEntries` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  <span data-ttu-id="cf12e-171">K testování kódu, stisknutím klávesy F5 zkompilování aplikace a pak klikněte na tlačítko **najít položky**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="cf12e-172">Klikněte na šipku rozevíracího seznamu ve <xref:System.Windows.Forms.ComboBox> k zobrazení vstupní data.</span><span class="sxs-lookup"><span data-stu-id="cf12e-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="cf12e-173">Vybrat a zobrazit jednotlivé položky</span><span class="sxs-lookup"><span data-stu-id="cf12e-173">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="cf12e-174">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `Display` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  <span data-ttu-id="cf12e-175">K testování kódu, stisknutím klávesy F5 kompilace aplikace a pak odeslat záznam.</span><span class="sxs-lookup"><span data-stu-id="cf12e-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="cf12e-176">Klikněte na tlačítko **najít položky**, vyberte položku z <xref:System.Windows.Forms.ComboBox>a potom klikněte na **zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="cf12e-177">Zobrazí obsah vybrané položky v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="cf12e-178">Povolení uživatelům odstranit nebo upravit položky</span><span class="sxs-lookup"><span data-stu-id="cf12e-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="cf12e-179">Nakonec můžete zahrnout další funkce umožňuje uživatelům odstranit nebo upravit položky pomocí `DeleteEntry` a `EditEntry` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="cf12e-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="cf12e-180">Obě tlačítka zůstanou neaktivní, pokud se zobrazí položka.</span><span class="sxs-lookup"><span data-stu-id="cf12e-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="cf12e-181">Přidání ovládacích prvků formuláře v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cf12e-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="cf12e-182">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="cf12e-182">Control</span></span>|<span data-ttu-id="cf12e-183">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cf12e-183">Properties</span></span>|<span data-ttu-id="cf12e-184">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="cf12e-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-185">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-185">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-186">**Text**</span></span><br /><br /> <span data-ttu-id="cf12e-187">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="cf12e-188">**Odstranit položku**</span><span class="sxs-lookup"><span data-stu-id="cf12e-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-189">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-189">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-190">**Text**</span></span><br /><br /> <span data-ttu-id="cf12e-191">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="cf12e-192">**Upravit položku**</span><span class="sxs-lookup"><span data-stu-id="cf12e-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="cf12e-193">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-193">**Name**</span></span><br /><br /> <span data-ttu-id="cf12e-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf12e-194">**Text**</span></span><br /><br /> <span data-ttu-id="cf12e-195">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="cf12e-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="cf12e-196">**Odeslání úpravy**</span><span class="sxs-lookup"><span data-stu-id="cf12e-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="cf12e-197">Chcete-li povolit odstranění a úpravy položek</span><span class="sxs-lookup"><span data-stu-id="cf12e-197">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="cf12e-198">Přidejte následující kód, který `Display` tlačítka <xref:System.Windows.Forms.Control.Click> událostí, po `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  <span data-ttu-id="cf12e-199">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `DeleteEntry` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  <span data-ttu-id="cf12e-200">Jakmile uživatel zobrazí položku, `EditEntry` aktivuje tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cf12e-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="cf12e-201">Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> události `Display` tlačítko po `DisplayEntry.Text = ReadString`.</span><span class="sxs-lookup"><span data-stu-id="cf12e-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  <span data-ttu-id="cf12e-202">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `EditEntry` tlačítko a přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="cf12e-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  <span data-ttu-id="cf12e-203">Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `SubmitEdit` tlačítko a přidejte následující kód</span><span class="sxs-lookup"><span data-stu-id="cf12e-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 <span data-ttu-id="cf12e-204">K testování kódu, stisknutím klávesy F5 kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf12e-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="cf12e-205">Klikněte na tlačítko **najít položky**, vyberte položku a pak klikněte na tlačítko **zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="cf12e-206">Položka se zobrazí v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="cf12e-207">Klikněte na tlačítko **upravte položku**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-207">Click **Edit Entry**.</span></span> <span data-ttu-id="cf12e-208">Položka se zobrazí v `Entry` <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cf12e-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="cf12e-209">Upravte položku v `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na tlačítko **odeslání upravit**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="cf12e-210">Otevřete `MyDiary.txt` souboru k ověření vašich oprav.</span><span class="sxs-lookup"><span data-stu-id="cf12e-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="cf12e-211">Nyní vyberte položku a klikněte na tlačítko **odstranit položku**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="cf12e-212">Když <xref:System.Windows.Forms.MessageBox> požádá o potvrzení, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf12e-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="cf12e-213">Zavřete aplikaci a otevřete `MyDiary.txt` potvrďte odstranění.</span><span class="sxs-lookup"><span data-stu-id="cf12e-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf12e-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf12e-214">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="cf12e-215">Návody</span><span class="sxs-lookup"><span data-stu-id="cf12e-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)

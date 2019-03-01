---
title: Ukládání dat do schránky a čtení ze schránky (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: cc39c501520f8d25d01917114553647621438750
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977705"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="64d1b-102">Ukládání dat do schránky a čtení ze schránky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64d1b-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="64d1b-103">Schránky slouží k ukládání dat, jako je například textu a obrázků.</span><span class="sxs-lookup"><span data-stu-id="64d1b-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="64d1b-104">Protože schránky sdílí všech aktivních procesů, lze použít k přenosu dat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="64d1b-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="64d1b-105">`My.Computer.Clipboard` Objekt umožňuje snadno přistupovat do schránky a číst z a do ní zapisovat.</span><span class="sxs-lookup"><span data-stu-id="64d1b-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="64d1b-106">Čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="64d1b-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="64d1b-107">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodu za účelem čtení textu do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="64d1b-108">Následující kód načte text a zobrazí ho v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="64d1b-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="64d1b-109">Musí existovat text ze schránky. například správně spustit.</span><span class="sxs-lookup"><span data-stu-id="64d1b-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="64d1b-110">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="64d1b-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="64d1b-111">V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**.</span><span class="sxs-lookup"><span data-stu-id="64d1b-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="64d1b-112">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="64d1b-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="64d1b-113">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodu pro načtení obrázku ze schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="64d1b-114">Tento příklad kontroluje, jestli je obrázek do schránky před načtením a ji přiřadíte `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="64d1b-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="64d1b-115">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="64d1b-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="64d1b-116">V dialogu pro výběr fragmentu kódu je umístěn v **formulářových aplikací Windows > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="64d1b-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="64d1b-117">Položky umístěné do schránky se zachová, i když je aplikace ukončena.</span><span class="sxs-lookup"><span data-stu-id="64d1b-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="64d1b-118">Určuje typ souboru je uložen do schránky</span><span class="sxs-lookup"><span data-stu-id="64d1b-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="64d1b-119">Data do schránky. může trvat několik různé podoby, jako je například text, zvukový soubor nebo obrázek.</span><span class="sxs-lookup"><span data-stu-id="64d1b-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="64d1b-120">Aby bylo možné zjistit, jaký typ souboru je do schránky, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="64d1b-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="64d1b-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu je možné použít, pokud máte vlastní formát, který chcete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="64d1b-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="64d1b-122">Použití `ContainsImage` funkce určuje, jestli data obsažená ve schránce je obrázek.</span><span class="sxs-lookup"><span data-stu-id="64d1b-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="64d1b-123">Následující kód zkontroluje, jestli se data bitovou kopii a odpovídajícím způsobem sestavy.</span><span class="sxs-lookup"><span data-stu-id="64d1b-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="64d1b-124">Vymazat schránku</span><span class="sxs-lookup"><span data-stu-id="64d1b-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="64d1b-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="64d1b-126">Protože schránky je sdílet s jinými procesy, zrušením zaškrtnutí může mít vliv na těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="64d1b-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="64d1b-127">Následující kód ukazuje způsob použití `Clear` metody.</span><span class="sxs-lookup"><span data-stu-id="64d1b-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="64d1b-128">Zápis do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="64d1b-129">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> způsob zápisu textu do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="64d1b-130">Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="64d1b-131">`SetText` Metoda přijímá parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="64d1b-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="64d1b-132">Následující kód zapíše řetězce "Toto je testovací řetězec" do schránky jako text ve formátu RTF.</span><span class="sxs-lookup"><span data-stu-id="64d1b-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="64d1b-133">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metody zapsat data do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="64d1b-134">Tento příklad zapíše `DataObject` `dataChunk` do schránky ve vlastním formátu `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="64d1b-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="64d1b-135">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metody zapsat zvuková data do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="64d1b-136">Tento příklad vytvoří pole bajtů `musicReader`, načte soubor `cool.wav` do ní a zapíše jej do schránky.</span><span class="sxs-lookup"><span data-stu-id="64d1b-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="64d1b-137">Protože schránky je přístupný ostatním uživatelům, nepoužívejte ho pro ukládání citlivých informací, jako jsou hesla nebo důvěrná data.</span><span class="sxs-lookup"><span data-stu-id="64d1b-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d1b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64d1b-138">See also</span></span>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="64d1b-139">Postupy: Čtení dat objektů ze souboru XML</span><span class="sxs-lookup"><span data-stu-id="64d1b-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="64d1b-140">Postupy: Zápis dat objektů do souboru XML</span><span class="sxs-lookup"><span data-stu-id="64d1b-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

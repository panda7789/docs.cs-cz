---
title: Ukládání dat do schránky a jejich čtení (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: d7693f6b5dc74e17686cd7d2667f32adbde9df80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916508"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="19b20-102">Ukládání dat do schránky a jejich čtení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19b20-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="19b20-103">Schránku lze použít k ukládání dat, jako je například text a obrázky.</span><span class="sxs-lookup"><span data-stu-id="19b20-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="19b20-104">Vzhledem k tomu, že schránka sdílí všechny aktivní procesy, lze ji použít k přenosu dat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="19b20-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="19b20-105">`My.Computer.Clipboard` Objekt umožňuje snadný přístup ke schránce a čtení z nich a zápis do ní.</span><span class="sxs-lookup"><span data-stu-id="19b20-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="19b20-106">Čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="19b20-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="19b20-107">K přečtení textu ve schránce použijte metodu.<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A></span><span class="sxs-lookup"><span data-stu-id="19b20-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="19b20-108">Následující kód přečte text a zobrazí jej v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="19b20-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="19b20-109">Ve schránce musí být uložený text, aby mohl být příklad správně spuštěn.</span><span class="sxs-lookup"><span data-stu-id="19b20-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="19b20-110">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="19b20-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="19b20-111">Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**.</span><span class="sxs-lookup"><span data-stu-id="19b20-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="19b20-112">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="19b20-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="19b20-113"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> Použijte metodu pro načtení obrázku ze schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="19b20-114">Tento příklad zkontroluje, zda je ve schránce k dispozici obrázek před jeho načtením a přiřazením k `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="19b20-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="19b20-115">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="19b20-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="19b20-116">Ve výběru fragmentu kódu se nachází v **model Windows Forms aplikace > schránka**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="19b20-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="19b20-117">Položky umístěné ve schránce zůstanou i po vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="19b20-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="19b20-118">Určení typu souboru uloženého ve schránce</span><span class="sxs-lookup"><span data-stu-id="19b20-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="19b20-119">Data ve schránce mohou mít řadu různých forem, jako je například text, zvukový soubor nebo obrázek.</span><span class="sxs-lookup"><span data-stu-id="19b20-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="19b20-120">Chcete-li určit, který soubor je ve schránce, můžete použít <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>jako například,, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="19b20-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="19b20-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu lze použít, pokud máte vlastní formát, který chcete kontrolovat.</span><span class="sxs-lookup"><span data-stu-id="19b20-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="19b20-122">`ContainsImage` Pomocí funkce určíte, zda jsou data obsažená ve schránce obrázkem.</span><span class="sxs-lookup"><span data-stu-id="19b20-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="19b20-123">Následující kód zkontroluje, zda se jedná o odpovídající obrázek a sestavy.</span><span class="sxs-lookup"><span data-stu-id="19b20-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="19b20-124">Vymazávání schránky</span><span class="sxs-lookup"><span data-stu-id="19b20-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="19b20-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže schránku.</span><span class="sxs-lookup"><span data-stu-id="19b20-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="19b20-126">Vzhledem k tomu, že schránka sdílí jiné procesy, její zrušení může mít vliv na tyto procesy.</span><span class="sxs-lookup"><span data-stu-id="19b20-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="19b20-127">Následující kód ukazuje, jak použít `Clear` metodu.</span><span class="sxs-lookup"><span data-stu-id="19b20-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="19b20-128">Zápis do schránky</span><span class="sxs-lookup"><span data-stu-id="19b20-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="19b20-129"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> Použijte metodu k zápisu textu do schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="19b20-130">Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="19b20-131">Metoda může přijmout parametr formátu, který obsahuje <xref:System.Windows.Forms.TextDataFormat>typ. `SetText`</span><span class="sxs-lookup"><span data-stu-id="19b20-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="19b20-132">Následující kód zapíše řetězec "Toto je testovací řetězec" do schránky jako text RTF.</span><span class="sxs-lookup"><span data-stu-id="19b20-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="19b20-133"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> Použijte metodu pro zápis dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="19b20-134">Tento příklad zapíše `DataObject` `dataChunk` do schránky ve vlastním formátu `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="19b20-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="19b20-135"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> Použijte metodu pro zápis zvukových dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="19b20-136">Tento příklad vytvoří bajtové pole `musicReader`, přečte soubor `cool.wav` do něj a pak ho zapíše do schránky.</span><span class="sxs-lookup"><span data-stu-id="19b20-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="19b20-137">Vzhledem k tomu, že je možné k schránce získat jiní uživatelé, nepoužívejte ji k ukládání citlivých informací, jako jsou hesla nebo důvěrná data.</span><span class="sxs-lookup"><span data-stu-id="19b20-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b20-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19b20-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="19b20-139">Postupy: Čtení dat objektů ze souboru XML</span><span class="sxs-lookup"><span data-stu-id="19b20-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="19b20-140">Postupy: Zápis dat objektů do souboru XML</span><span class="sxs-lookup"><span data-stu-id="19b20-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

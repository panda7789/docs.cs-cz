---
title: "Ukládání dat do schránky a čtení ze schránky (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7bb4ad56f0a039aa7b23d7f0612aaab9366cb9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="2e4b4-102">Ukládání dat do schránky a čtení ze schránky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e4b4-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="2e4b4-103">Schránky slouží k ukládání dat, jako je například textu a obrázků.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="2e4b4-104">Protože schránky je sdílen všech aktivních procesů, může sloužit k přenosu dat mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="2e4b4-105">`My.Computer.Clipboard` Objekt umožňuje snadno přistupovat do schránky a čtení z a do něj zapisovat.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="2e4b4-106">Čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="2e4b4-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="2e4b4-107">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodu za účelem čtení textu do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="2e4b4-108">Následující kód načte text a zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="2e4b4-109">Musí být uložen do schránky například správné fungování text.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 <span data-ttu-id="2e4b4-110">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2e4b4-111">V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > schránky**.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="2e4b4-112">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2e4b4-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="2e4b4-113">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodu pro načtení obrázku ze schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="2e4b4-114">Tento příklad zkontroluje, pokud je bitovou kopii do schránky před jeho načítání a jeho k přiřazení `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 <span data-ttu-id="2e4b4-115">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2e4b4-116">V Sběrač fragmentů kódu je umístěn v **aplikacích Windows Forms > schránky**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2e4b4-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="2e4b4-117">Položky, které jsou umístěny do schránky zachová i po ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="2e4b4-118">Určení typu souboru uložen do schránky</span><span class="sxs-lookup"><span data-stu-id="2e4b4-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="2e4b4-119">Data do schránky může trvat několik různých formulářů, například textu, zvukových souborů nebo bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="2e4b4-120">Chcete-li zjistit, jaký typ souboru je do schránky, můžete použít metody, jako <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, a <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="2e4b4-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metodu lze použít, pokud máte vlastní formát, který chcete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="2e4b4-122">Použití `ContainsImage` funkce k určení, zda data obsažená ve schránce je bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="2e4b4-123">Následující kód zkontroluje, zda jsou data bitovou kopii a odpovídajícím způsobem sestavy.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="2e4b4-124">Vymazání schránky</span><span class="sxs-lookup"><span data-stu-id="2e4b4-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="2e4b4-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda vymaže do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="2e4b4-126">Protože schránky je sdílet s jinými procesy, vymazáním může mít vliv na těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="2e4b4-127">Následující kód ukazuje způsob použití `Clear` metoda.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="2e4b4-128">Zápis do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="2e4b4-129">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodu pro zápis textu do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="2e4b4-130">Následující kód zapíše řetězec "Toto je test řetězec" do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 <span data-ttu-id="2e4b4-131">`SetText` Metoda může přijmout parametr formátu, který obsahuje typ <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="2e4b4-132">Následující kód zapíše řetězec "Toto je test řetězec" do schránky jako text ve formátu RTF.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <span data-ttu-id="2e4b4-133">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metoda zapsat data do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="2e4b4-134">Tento příklad zapíše `DataObject``dataChunk` do schránky ve vlastním formátu `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-134">This example writes the `DataObject``dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <span data-ttu-id="2e4b4-135">Použití <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metoda zapsat zvuk data do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="2e4b4-136">Tento příklad vytvoří bajtové pole `musicReader`, načte soubor `cool.wav` do ní a zapíše ho do schránky.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e4b4-137">Protože schránky můžete mít přístup další uživatelé, nepoužívejte ho pro uložení citlivé informace, třeba hesla nebo důvěrné údaje.</span><span class="sxs-lookup"><span data-stu-id="2e4b4-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e4b4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e4b4-138">See also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [<span data-ttu-id="2e4b4-139">Postupy: čtení dat objektů ze souboru XML</span><span class="sxs-lookup"><span data-stu-id="2e4b4-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="2e4b4-140">Postupy: zápis dat objektů do souboru XML</span><span class="sxs-lookup"><span data-stu-id="2e4b4-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

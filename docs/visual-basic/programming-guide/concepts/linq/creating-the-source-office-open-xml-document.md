---
title: "Vytvoření zdrojového dokumentu XML otevřete Office (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c573f703ea3d7550dabd994f538e28e197874715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="f7e10-102">Vytvoření zdrojového dokumentu XML otevřete Office (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7e10-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="f7e10-103">Toto téma ukazuje, jak vytvořit dokument XML WordprocessingML otevřete Office, používaných v předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="f7e10-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="f7e10-104">Pokud budete postupovat podle těchto pokynů, bude odpovídat výstupu výstupu, zadané v obou příkladech.</span><span class="sxs-lookup"><span data-stu-id="f7e10-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="f7e10-105">V příkladech v tomto kurzu však bude fungovat s platnou WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7e10-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="f7e10-106">Vytvoření dokumentu, který tento kurz používá, musí mít Microsoft Office 2007 nebo novější nebo Microsoft Office 2003 pomocí sady Microsoft Office kompatibility Pack musí mít pro Word, Excel a PowerPoint formáty souborů 2007.</span><span class="sxs-lookup"><span data-stu-id="f7e10-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="f7e10-107">Vytváření WordprocessingML dokumentu</span><span class="sxs-lookup"><span data-stu-id="f7e10-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="f7e10-108">Chcete-li vytvořit WordprocessingML dokumentu</span><span class="sxs-lookup"><span data-stu-id="f7e10-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="f7e10-109">Vytvoříte nový textový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="f7e10-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="f7e10-110">Vložte následující text do nového dokumentu:</span><span class="sxs-lookup"><span data-stu-id="f7e10-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="f7e10-111">Formát první řádek s styl "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="f7e10-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="f7e10-112">Vyberte řádky, které obsahují kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7e10-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="f7e10-113">První řádek začíná `Imports` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f7e10-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="f7e10-114">Poslední řádek je "End Class".</span><span class="sxs-lookup"><span data-stu-id="f7e10-114">The last line is "End Class".</span></span> <span data-ttu-id="f7e10-115">Formátování řádků s Kurýrní písmo.</span><span class="sxs-lookup"><span data-stu-id="f7e10-115">Format the lines with the courier font.</span></span> <span data-ttu-id="f7e10-116">Formátovat pomocí nového stylu a pojmenujte nový styl "Kódu".</span><span class="sxs-lookup"><span data-stu-id="f7e10-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="f7e10-117">Nakonec vyberte celý řádek, který obsahuje výstup a naformátujte ho pomocí `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="f7e10-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="f7e10-118">Uložte dokument a pojmenujte ji SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="f7e10-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7e10-119">Pokud používáte aplikace Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7e10-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e10-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7e10-120">See Also</span></span>  
 [<span data-ttu-id="f7e10-121">Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7e10-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

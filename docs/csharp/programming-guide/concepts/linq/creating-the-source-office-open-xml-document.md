---
title: Vytvoření zdrojového dokumentu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: c5884d1e34558d01be4c873c3f44222396e588ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324496"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="5a2a4-102">Vytvoření zdrojového dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a2a4-102">Creating the Source Office Open XML Document (C#)</span></span>
<span data-ttu-id="5a2a4-103">Toto téma ukazuje, jak vytvořit dokument XML WordprocessingML otevřete Office, používaných v předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="5a2a4-104">Pokud budete postupovat podle těchto pokynů, bude odpovídat výstupu výstupu, zadané v obou příkladech.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="5a2a4-105">V příkladech v tomto kurzu však bude fungovat s platnou WordprocessingML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="5a2a4-106">Vytvoření dokumentu, který tento kurz používá, musí mít Microsoft Office 2007 nebo novější nebo Microsoft Office 2003 pomocí sady Microsoft Office kompatibility Pack musí mít pro Word, Excel a PowerPoint formáty souborů 2007.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="5a2a4-107">Vytváření WordprocessingML dokumentu</span><span class="sxs-lookup"><span data-stu-id="5a2a4-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="5a2a4-108">Chcete-li vytvořit WordprocessingML dokumentu</span><span class="sxs-lookup"><span data-stu-id="5a2a4-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="5a2a4-109">Vytvoříte nový textový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="5a2a4-110">Vložte následující text do nového dokumentu:</span><span class="sxs-lookup"><span data-stu-id="5a2a4-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="5a2a4-111">Formát první řádek s styl "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="5a2a4-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="5a2a4-112">Vyberte řádky, které obsahují kódu C#.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="5a2a4-113">První řádek začíná `using` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="5a2a4-114">Poslední řádek je poslední složená závorka.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-114">The last line is the last closing brace.</span></span> <span data-ttu-id="5a2a4-115">Formátování řádků s Kurýrní písmo.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-115">Format the lines with the courier font.</span></span> <span data-ttu-id="5a2a4-116">Formátovat pomocí nového stylu a pojmenujte nový styl "Kódu".</span><span class="sxs-lookup"><span data-stu-id="5a2a4-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="5a2a4-117">Nakonec vyberte celý řádek, který obsahuje výstup a naformátujte ho pomocí `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="5a2a4-118">Uložte dokument a pojmenujte ji SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a2a4-119">Pokud používáte aplikace Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="5a2a4-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2a4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a2a4-120">See Also</span></span>  
 [<span data-ttu-id="5a2a4-121">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a2a4-121">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

---
title: Vytvoření zdrojového dokumentu Office Open XML
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410835"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="7f9e8-102">Vytvoření zdrojového dokumentu XML pro Office Open Source (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9e8-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="7f9e8-103">V tomto tématu se dozvíte, jak vytvořit dokument Office Open XML WordprocessingML, který se používá v dalších příkladech tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="7f9e8-104">Pokud budete postupovat podle těchto pokynů, váš výstup bude odpovídat výstupu uvedenému v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="7f9e8-105">Příklady v tomto kurzu ale budou fungovat s jakýmkoli platným dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="7f9e8-106">Pokud chcete vytvořit dokument, který používá tento kurz, musíte mít nainstalovanou systém Microsoft Office 2007 nebo novější, nebo musíte mít systém Microsoft Office 2003 pomocí sady systém Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formats.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="7f9e8-107">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="7f9e8-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="7f9e8-108">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="7f9e8-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="7f9e8-109">Vytvoří nový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="7f9e8-110">Vložte do nového dokumentu následující text:</span><span class="sxs-lookup"><span data-stu-id="7f9e8-110">Paste the following text into the new document:</span></span>  
  
    ```text  
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
  
3. <span data-ttu-id="7f9e8-111">Naformátuje první řádek stylem "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="7f9e8-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="7f9e8-112">Vyberte řádky, které obsahují kód Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="7f9e8-113">První řádek začíná `Imports` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="7f9e8-114">Poslední řádek je "End Class".</span><span class="sxs-lookup"><span data-stu-id="7f9e8-114">The last line is "End Class".</span></span> <span data-ttu-id="7f9e8-115">Naformátujte čáry pomocí písma Courier.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-115">Format the lines with the courier font.</span></span> <span data-ttu-id="7f9e8-116">Naformátujte je pomocí nového stylu a pojmenujte nový styl "Code".</span><span class="sxs-lookup"><span data-stu-id="7f9e8-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="7f9e8-117">Nakonec vyberte celý řádek obsahující výstup a naformátujte ho pomocí `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="7f9e8-118">Uložte dokument a pojmenujte ho SampleDoc. docx.</span><span class="sxs-lookup"><span data-stu-id="7f9e8-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7f9e8-119">Pokud používáte Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** možnost **dokument Word 2007** .</span><span class="sxs-lookup"><span data-stu-id="7f9e8-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9e8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f9e8-120">See also</span></span>

- [<span data-ttu-id="7f9e8-121">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9e8-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)

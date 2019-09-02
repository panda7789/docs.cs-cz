---
title: Vytvoření zdrojového dokumentuC#XML pro Office Open
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204154"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="ad0ba-102">Vytvoření zdrojového dokumentuC#XML pro Office Open</span><span class="sxs-lookup"><span data-stu-id="ad0ba-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="ad0ba-103">V tomto tématu se dozvíte, jak vytvořit dokument Office Open XML WordprocessingML, který se používá v dalších příkladech tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="ad0ba-104">Pokud budete postupovat podle těchto pokynů, váš výstup bude odpovídat výstupu uvedenému v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="ad0ba-105">Příklady v tomto kurzu ale budou fungovat s jakýmkoli platným dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="ad0ba-106">Pokud chcete vytvořit dokument, který používá tento kurz, musíte mít nainstalovanou systém Microsoft Office 2007 nebo novější, nebo musíte mít systém Microsoft Office 2003 pomocí sady systém Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formats.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="ad0ba-107">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ad0ba-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="ad0ba-108">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ad0ba-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="ad0ba-109">Vytvoří nový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="ad0ba-110">Vložte do nového dokumentu následující text:</span><span class="sxs-lookup"><span data-stu-id="ad0ba-110">Paste the following text into the new document:</span></span>

    ```text
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

3. <span data-ttu-id="ad0ba-111">Naformátuje první řádek stylem "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="ad0ba-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="ad0ba-112">Vyberte řádky, které obsahují C# kód.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="ad0ba-113">První řádek začíná `using` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="ad0ba-114">Poslední řádek představuje poslední pravou závorku.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-114">The last line is the last closing brace.</span></span> <span data-ttu-id="ad0ba-115">Naformátujte čáry pomocí písma Courier.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-115">Format the lines with the courier font.</span></span> <span data-ttu-id="ad0ba-116">Naformátujte je pomocí nového stylu a pojmenujte nový styl "Code".</span><span class="sxs-lookup"><span data-stu-id="ad0ba-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="ad0ba-117">Nakonec vyberte celý řádek obsahující výstup a naformátujte ho pomocí `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="ad0ba-118">Uložte dokument a pojmenujte ho SampleDoc. docx.</span><span class="sxs-lookup"><span data-stu-id="ad0ba-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad0ba-119">Pokud používáte Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** možnost **dokument Word 2007** .</span><span class="sxs-lookup"><span data-stu-id="ad0ba-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

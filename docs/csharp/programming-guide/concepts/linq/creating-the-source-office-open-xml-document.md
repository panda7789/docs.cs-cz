---
title: Vytvoření zdrojového dokumentu XML s otevřeným jazykem Office (C#)
description: Vytvoření dokumentu Office Open XML WordprocessingML pro použití s kurzy C# Tento článek vyžaduje systém Microsoft Office.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103992"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="323e8-104">Vytvoření zdrojového dokumentu XML s otevřeným jazykem Office (C#)</span><span class="sxs-lookup"><span data-stu-id="323e8-104">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="323e8-105">V tomto tématu se dozvíte, jak vytvořit dokument Office Open XML WordprocessingML, který se používá v dalších příkladech tohoto kurzu.</span><span class="sxs-lookup"><span data-stu-id="323e8-105">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="323e8-106">Pokud budete postupovat podle těchto pokynů, váš výstup bude odpovídat výstupu uvedenému v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="323e8-106">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="323e8-107">Příklady v tomto kurzu ale budou fungovat s jakýmkoli platným dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="323e8-107">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="323e8-108">Pokud chcete vytvořit dokument, který používá tento kurz, musíte mít nainstalovanou systém Microsoft Office 2007 nebo novější, nebo musíte mít systém Microsoft Office 2003 pomocí sady systém Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formats.</span><span class="sxs-lookup"><span data-stu-id="323e8-108">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="323e8-109">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="323e8-109">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="323e8-110">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="323e8-110">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="323e8-111">Vytvoří nový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="323e8-111">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="323e8-112">Vložte do nového dokumentu následující text:</span><span class="sxs-lookup"><span data-stu-id="323e8-112">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="323e8-113">Naformátuje první řádek stylem "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="323e8-113">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="323e8-114">Vyberte řádky, které obsahují kód jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="323e8-114">Select the lines that contain the C# code.</span></span> <span data-ttu-id="323e8-115">První řádek začíná `using` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="323e8-115">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="323e8-116">Poslední řádek představuje poslední pravou závorku.</span><span class="sxs-lookup"><span data-stu-id="323e8-116">The last line is the last closing brace.</span></span> <span data-ttu-id="323e8-117">Naformátujte čáry pomocí písma Courier.</span><span class="sxs-lookup"><span data-stu-id="323e8-117">Format the lines with the courier font.</span></span> <span data-ttu-id="323e8-118">Naformátujte je pomocí nového stylu a pojmenujte nový styl "Code".</span><span class="sxs-lookup"><span data-stu-id="323e8-118">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="323e8-119">Nakonec vyberte celý řádek obsahující výstup a naformátujte ho pomocí `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="323e8-119">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="323e8-120">Uložte dokument a pojmenujte ho SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="323e8-120">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="323e8-121">Pokud používáte Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** možnost **dokument Word 2007** .</span><span class="sxs-lookup"><span data-stu-id="323e8-121">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

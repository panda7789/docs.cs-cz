---
title: Vytvoření dokumentu Open XML zdrojové kanceláře (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204154"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="16603-102">Vytvoření dokumentu Open XML zdrojové kanceláře (C#)</span><span class="sxs-lookup"><span data-stu-id="16603-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="16603-103">Toto téma ukazuje, jak vytvořit dokument Office Open XML WordprocessingML, který používají další příklady v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="16603-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="16603-104">Pokud budete postupovat podle těchto pokynů, výstup bude odpovídat výstupu uvedenému v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="16603-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="16603-105">Příklady v tomto kurzu však bude fungovat s platným dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="16603-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="16603-106">Chcete-li vytvořit dokument, který tento kurz používá, musíte mít nainstalovány sady Microsoft Office 2007 nebo novější nebo sadu Microsoft Office 2003 s kompatibilní sadou Microsoft Office Compatibility Pack pro formáty souborů aplikace Word, Excel a PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="16603-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="16603-107">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="16603-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="16603-108">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="16603-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="16603-109">Vytvořte nový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="16603-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="16603-110">Vložte do nového dokumentu následující text:</span><span class="sxs-lookup"><span data-stu-id="16603-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="16603-111">Naformátujte první řádek stylem "Nadpis 1".</span><span class="sxs-lookup"><span data-stu-id="16603-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="16603-112">Vyberte řádky, které obsahují kód Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="16603-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="16603-113">První řádek začíná `using` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="16603-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="16603-114">Poslední řádek je poslední uzavírací závorka.</span><span class="sxs-lookup"><span data-stu-id="16603-114">The last line is the last closing brace.</span></span> <span data-ttu-id="16603-115">Naformátujte řádky písmem kurýra.</span><span class="sxs-lookup"><span data-stu-id="16603-115">Format the lines with the courier font.</span></span> <span data-ttu-id="16603-116">Naformátujte je novým stylem a pojmenujte nový styl "Kód".</span><span class="sxs-lookup"><span data-stu-id="16603-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="16603-117">Nakonec vyberte celý řádek, který obsahuje výstup, `Code` a naformátujte jej stylem.</span><span class="sxs-lookup"><span data-stu-id="16603-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="16603-118">Uložte dokument a pojmenujte jej SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="16603-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16603-119">Pokud používáte aplikaci Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** dokument aplikace Word **2007.**</span><span class="sxs-lookup"><span data-stu-id="16603-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

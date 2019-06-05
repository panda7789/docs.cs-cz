---
title: Vytvoření zdrojového dokumentu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 024b6c80cdedf38fd2dcee77562c0105df7bd033
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690106"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="ddc98-102">Vytvoření zdrojového dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ddc98-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="ddc98-103">Toto téma ukazuje, jak vytvořit dokumentu Office Open XML WordprocessingML, použít další příklady v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="ddc98-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="ddc98-104">Pokud budete postupovat podle těchto pokynů, výstup bude odpovídat výstup poskytovaný v každém příkladu.</span><span class="sxs-lookup"><span data-stu-id="ddc98-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="ddc98-105">Příklady v tomto kurzu ale bude fungovat s libovolný platný dokument WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="ddc98-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="ddc98-106">Vytvoření dokumentu, který tento kurz používá, musí mít buď Microsoft Office 2007 nebo novější, nebo musí mít Microsoft Office 2003 Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formátů.</span><span class="sxs-lookup"><span data-stu-id="ddc98-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="ddc98-107">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ddc98-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="ddc98-108">Vytvoření dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ddc98-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="ddc98-109">Vytvoříte nový textový dokument aplikace Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="ddc98-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="ddc98-110">Vložte následující text do nového dokumentu:</span><span class="sxs-lookup"><span data-stu-id="ddc98-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="ddc98-111">Naformátuje styl "Nadpis 1" na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="ddc98-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="ddc98-112">Vyberte řádky, které obsahují kód jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ddc98-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="ddc98-113">První řádek začíná `using` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ddc98-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="ddc98-114">Poslední řádek je poslední pravou složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="ddc98-114">The last line is the last closing brace.</span></span> <span data-ttu-id="ddc98-115">Formátování řádků s Kurýrní písma.</span><span class="sxs-lookup"><span data-stu-id="ddc98-115">Format the lines with the courier font.</span></span> <span data-ttu-id="ddc98-116">Formát se nový styl a pojmenujte nový styl "Kód".</span><span class="sxs-lookup"><span data-stu-id="ddc98-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="ddc98-117">Nakonec označit celý řádek, který obsahuje výstup a naformátovat ho `Code` style.</span><span class="sxs-lookup"><span data-stu-id="ddc98-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="ddc98-118">Uložte dokument a pojmenujte ho SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="ddc98-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ddc98-119">Pokud používáte aplikaci Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="ddc98-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

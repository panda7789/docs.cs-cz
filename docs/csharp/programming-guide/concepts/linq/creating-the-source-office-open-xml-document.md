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
# <a name="creating-the-source-office-open-xml-document-c"></a>Vytvoření zdrojového dokumentu XML s otevřeným jazykem Office (C#)

V tomto tématu se dozvíte, jak vytvořit dokument Office Open XML WordprocessingML, který se používá v dalších příkladech tohoto kurzu. Pokud budete postupovat podle těchto pokynů, váš výstup bude odpovídat výstupu uvedenému v každém příkladu.

Příklady v tomto kurzu ale budou fungovat s jakýmkoli platným dokumentem WordprocessingML.

Pokud chcete vytvořit dokument, který používá tento kurz, musíte mít nainstalovanou systém Microsoft Office 2007 nebo novější, nebo musíte mít systém Microsoft Office 2003 pomocí sady systém Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formats.

## <a name="creating-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

#### <a name="to-create-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

1. Vytvoří nový dokument aplikace Microsoft Word.

2. Vložte do nového dokumentu následující text:

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

3. Naformátuje první řádek stylem "Nadpis 1".

4. Vyberte řádky, které obsahují kód jazyka C#. První řádek začíná `using` klíčovým slovem. Poslední řádek představuje poslední pravou závorku. Naformátujte čáry pomocí písma Courier. Naformátujte je pomocí nového stylu a pojmenujte nový styl "Code".

5. Nakonec vyberte celý řádek obsahující výstup a naformátujte ho pomocí `Code` stylu.

6. Uložte dokument a pojmenujte ho SampleDoc.docx.

    > [!NOTE]
    > Pokud používáte Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** možnost **dokument Word 2007** .

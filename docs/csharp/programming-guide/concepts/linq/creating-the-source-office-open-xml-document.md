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
# <a name="creating-the-source-office-open-xml-document-c"></a>Vytvoření dokumentu Open XML zdrojové kanceláře (C#)

Toto téma ukazuje, jak vytvořit dokument Office Open XML WordprocessingML, který používají další příklady v tomto kurzu. Pokud budete postupovat podle těchto pokynů, výstup bude odpovídat výstupu uvedenému v každém příkladu.

Příklady v tomto kurzu však bude fungovat s platným dokumentem WordprocessingML.

Chcete-li vytvořit dokument, který tento kurz používá, musíte mít nainstalovány sady Microsoft Office 2007 nebo novější nebo sadu Microsoft Office 2003 s kompatibilní sadou Microsoft Office Compatibility Pack pro formáty souborů aplikace Word, Excel a PowerPoint 2007.

## <a name="creating-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

#### <a name="to-create-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

1. Vytvořte nový dokument aplikace Microsoft Word.

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

3. Naformátujte první řádek stylem "Nadpis 1".

4. Vyberte řádky, které obsahují kód Jazyka C#. První řádek začíná `using` klíčovým slovem. Poslední řádek je poslední uzavírací závorka. Naformátujte řádky písmem kurýra. Naformátujte je novým stylem a pojmenujte nový styl "Kód".

5. Nakonec vyberte celý řádek, který obsahuje výstup, `Code` a naformátujte jej stylem.

6. Uložte dokument a pojmenujte jej SampleDoc.docx.

    > [!NOTE]
    > Pokud používáte aplikaci Microsoft Word 2003, vyberte v rozevíracím seznamu **Uložit jako typ** dokument aplikace Word **2007.**

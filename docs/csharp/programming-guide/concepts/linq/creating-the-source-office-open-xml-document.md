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
# <a name="creating-the-source-office-open-xml-document-c"></a>Vytvoření zdrojového dokumentu Office Open XML (C#)

Toto téma ukazuje, jak vytvořit dokumentu Office Open XML WordprocessingML, použít další příklady v tomto kurzu. Pokud budete postupovat podle těchto pokynů, výstup bude odpovídat výstup poskytovaný v každém příkladu.

Příklady v tomto kurzu ale bude fungovat s libovolný platný dokument WordprocessingML.

Vytvoření dokumentu, který tento kurz používá, musí mít buď Microsoft Office 2007 nebo novější, nebo musí mít Microsoft Office 2003 Microsoft Office Compatibility Pack pro Word, Excel a PowerPoint 2007 formátů.

## <a name="creating-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

#### <a name="to-create-the-wordprocessingml-document"></a>Vytvoření dokumentu WordprocessingML

1. Vytvoříte nový textový dokument aplikace Microsoft Word.

2. Vložte následující text do nového dokumentu:

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

3. Naformátuje styl "Nadpis 1" na prvním řádku.

4. Vyberte řádky, které obsahují kód jazyka C#. První řádek začíná `using` – klíčové slovo. Poslední řádek je poslední pravou složenou závorku. Formátování řádků s Kurýrní písma. Formát se nový styl a pojmenujte nový styl "Kód".

5. Nakonec označit celý řádek, který obsahuje výstup a naformátovat ho `Code` style.

6. Uložte dokument a pojmenujte ho SampleDoc.docx.

    > [!NOTE]
    > Pokud používáte aplikaci Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.

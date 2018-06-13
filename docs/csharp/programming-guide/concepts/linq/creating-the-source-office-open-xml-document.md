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
# <a name="creating-the-source-office-open-xml-document-c"></a>Vytvoření zdrojového dokumentu Office Open XML (C#)
Toto téma ukazuje, jak vytvořit dokument XML WordprocessingML otevřete Office, používaných v předchozích příkladech v tomto kurzu. Pokud budete postupovat podle těchto pokynů, bude odpovídat výstupu výstupu, zadané v obou příkladech.  
  
 V příkladech v tomto kurzu však bude fungovat s platnou WordprocessingML dokumentu.  
  
 Vytvoření dokumentu, který tento kurz používá, musí mít Microsoft Office 2007 nebo novější nebo Microsoft Office 2003 pomocí sady Microsoft Office kompatibility Pack musí mít pro Word, Excel a PowerPoint formáty souborů 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Vytváření WordprocessingML dokumentu  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Chcete-li vytvořit WordprocessingML dokumentu  
  
1.  Vytvoříte nový textový dokument aplikace Microsoft Word.  
  
2.  Vložte následující text do nového dokumentu:  
  
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
  
3.  Formát první řádek s styl "Nadpis 1".  
  
4.  Vyberte řádky, které obsahují kódu C#. První řádek začíná `using` – klíčové slovo. Poslední řádek je poslední složená závorka. Formátování řádků s Kurýrní písmo. Formátovat pomocí nového stylu a pojmenujte nový styl "Kódu".  
  
5.  Nakonec vyberte celý řádek, který obsahuje výstup a naformátujte ho pomocí `Code` stylu.  
  
6.  Uložte dokument a pojmenujte ji SampleDoc.docx.  
  
    > [!NOTE]
    >  Pokud používáte aplikace Microsoft Word 2003, vyberte **dokument aplikace Word 2007** v **uložit jako typ** rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

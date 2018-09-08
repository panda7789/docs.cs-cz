---
title: LINQ to Objects (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 87c804a831272b2a0c08ac85a552fec86d665e7f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185464"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Termín "LINQ na objekty" odkazuje na použití odkazu LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující zprostředkovatele LINQ nebo rozhraní API, jako [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). LINQ můžete použít k dotazování všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být uživatelem definované nebo mohou být vráceny rozhraní API .NET Framework.  
  
 V základní smysl představuje LINQ to Objects nový přístup ke kolekcím. Starý způsob jste museli psát složité `For Each` smyček, které zadaná jak načíst data z kolekce. U přístupu s LINQ napíšete deklarativního kódu, který popisuje, co chcete načíst.  
  
 Kromě toho dotazů LINQ nabízejí tři hlavní výhody oproti tradičním `For Each` smyček:  
  
1.  Jsou stručnějším a čitelnějším, zejména v případě, že filtrování více podmínek.  
  
2.  Poskytují efektivní filtrování, řazení a seskupování schopností minimální kódu aplikace.  
  
3.  Může být přenést k jiným zdrojům dat s téměř nebo vůbec žádné změny.  
  
 Obecně platí, tím složitější operace, které chcete provést na datech, další výhody značným s využitím jazyka LINQ místo iterace tradiční techniky.  
  
 Cílem této části je předvést přístup LINQ s příklady vyberte. Není určena být vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Tento článek vysvětluje použití LINQ na dotazování a transformaci řetězce a kolekce řetězců. Obsahuje také odkazy na témata, která ukazují tyto zásady.  
  
 [LINQ a reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Obsahuje odkazy na ukázky, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů. Obsahuje také odkazy na témata, které předvádějí koncepce.  
  
 [Postupy: vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Demonstruje postup vytvoření dotazu na ArrayList v jazyce C#.  
  
 [Postupy: přidávání vlastních metod do dotazů LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a příklady kódu, které provádějí dotazy.

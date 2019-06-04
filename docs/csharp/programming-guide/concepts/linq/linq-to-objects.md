---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c66a818d48316279817fdc6b7919a7667b6b8eb8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484474"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
Termín "LINQ na objekty" odkazuje na použití odkazu LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující zprostředkovatele LINQ nebo rozhraní API, jako [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md). LINQ můžete použít k dotazování všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být uživatelem definované nebo mohou být vráceny rozhraní API .NET Framework.  
  
 V základní smysl představuje LINQ to Objects nový přístup ke kolekcím. Starý způsob jste museli psát složité `foreach` smyček, které zadaná jak načíst data z kolekce. U přístupu s LINQ napíšete deklarativního kódu, který popisuje, co chcete načíst.  
  
 Kromě toho dotazů LINQ nabízejí tři hlavní výhody oproti tradičním `foreach` smyček:  
  
1. Jsou stručnějším a čitelnějším, zejména v případě, že filtrování více podmínek.  
  
2. Poskytují efektivní filtrování, řazení a seskupování schopností minimální kódu aplikace.  
  
3. Může být přenést k jiným zdrojům dat s téměř nebo vůbec žádné změny.  
  
 Obecně platí, tím složitější operace, které chcete provést na datech, další výhody značným s využitím jazyka LINQ místo iterace tradiční techniky.  
  
 Cílem této části je předvést přístup LINQ s příklady vyberte. Není určena být vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 Tento článek vysvětluje použití LINQ na dotazování a transformaci řetězce a kolekce řetězců. Obsahuje také odkazy na témata, která ukazují tyto zásady.  
  
 [LINQ a reflexe (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 Obsahuje odkazy na ukázky, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů. Obsahuje také odkazy na témata, které předvádějí koncepce.  
  
 [Postupy: Vytvoření dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Demonstruje postup vytvoření dotazu na ArrayList v jazyce C#.  
  
 [Postupy: Přidávání vlastních metod do dotazů LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a příklady kódu, které provádějí dotazy.

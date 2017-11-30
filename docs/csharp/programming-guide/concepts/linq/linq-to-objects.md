---
title: LINQ na objekty (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bb2a6593b02125478f2221a6822dec447921c4f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-objects-c"></a>LINQ na objekty (C#)
Termín "LINQ na objekty" odkazuje na použití LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující LINQ zprostředkovatele nebo rozhraní API jako třeba [technologie LINQ to SQL](https://msdn.microsoft.com/library/bb386976) nebo [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). LINQ můžete použít k dotazování všechny vyčíslitelná kolekce, jako <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být definovaný uživatelem, nebo mohou být vráceny rozhraní API rozhraní .NET Framework.  
  
 LINQ na objekty v základní smysl, představuje nový přístup do kolekcí. Původní způsobem, jste museli zápisu komplexní `foreach` smyčky zadaných postup načtení dat z kolekce. V metodě LINQ zápisu deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazů LINQ nabízí tři hlavní výhody přes tradiční `foreach` smyčky:  
  
1.  Jsou více stručná a čitelná, zejména v případě, že filtrování více podmínek.  
  
2.  Poskytují výkonný filtrování, řazení a seskupování možnosti s minimální kódu aplikace.  
  
3.  Může být přesně do jiné zdroje dat se žádné nebo téměř žádné změny.  
  
 Obecně platí, tím složitější operace, kterou chcete provést na datech, další výhody zjistíte pomocí LINQ místo tradiční iterace techniky.  
  
 Účelem této části je za účelem ukázky LINQ přístup s příklady vyberte. Rozhraní není určeno jako vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 Vysvětluje, jak lze pro dotazování a Transformace řetězců a kolekcí řetězců LINQ. Taky obsahuje odkazy na témata, která ukazují tyto zásady.  
  
 [LINQ a reflexe (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 Odkazy na vzorku, který ukazuje, jak LINQ používá reflexe.  
  
 [LINQ a souborové adresáře (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů. Taky obsahuje odkazy na témata, která ukazují tyto koncepty.  
  
 [Postupy: dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak dotazu na ArrayList v jazyce C#.  
  
 [Postupy: Přidání vlastních metod pro dotazů LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 Obsahuje odkazy na témata, která popisují LINQ a zadejte příklady kódu, které provádět dotazy.

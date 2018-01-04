---
title: LINQ na objekty (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2a48e792c656a84c07730b67f734f6b539ab97d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linq-to-objects-visual-basic"></a>LINQ na objekty (Visual Basic)
Termín "LINQ na objekty" odkazuje na použití LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující LINQ zprostředkovatele nebo rozhraní API jako třeba [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). LINQ můžete použít k dotazování všechny vyčíslitelná kolekce, jako <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být definovaný uživatelem, nebo mohou být vráceny rozhraní API rozhraní .NET Framework.  
  
 LINQ na objekty v základní smysl, představuje nový přístup do kolekcí. Původní způsobem, jste museli zápisu komplexní `For Each` smyčky zadaných postup načtení dat z kolekce. V metodě LINQ zápisu deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazů LINQ nabízí tři hlavní výhody přes tradiční `For Each` smyčky:  
  
1.  Jsou více stručná a čitelná, zejména v případě, že filtrování více podmínek.  
  
2.  Poskytují výkonný filtrování, řazení a seskupování možnosti s minimální kódu aplikace.  
  
3.  Může být přesně do jiné zdroje dat se žádné nebo téměř žádné změny.  
  
 Obecně platí, tím složitější operace, kterou chcete provést na datech, další výhody zjistíte pomocí LINQ místo tradiční iterace techniky.  
  
 Účelem této části je za účelem ukázky LINQ přístup s příklady vyberte. Rozhraní není určeno jako vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Vysvětluje, jak lze pro dotazování a Transformace řetězců a kolekcí řetězců LINQ. Taky obsahuje odkazy na témata, která ukazují tyto zásady.  
  
 [LINQ a reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Odkazy na vzorku, který ukazuje, jak LINQ používá reflexe.  
  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů. Taky obsahuje odkazy na témata, která ukazují tyto koncepty.  
  
 [Postupy: dotazu na ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak dotazu na ArrayList v jazyce C#.  
  
 [Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Obsahuje odkazy na témata, která popisují LINQ a zadejte příklady kódu, které provádět dotazy.

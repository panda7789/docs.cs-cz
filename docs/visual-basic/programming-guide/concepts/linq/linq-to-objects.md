---
title: LINQ na objekty
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 1dca449f12c312fd395be56ebcb426c3a63b64d0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369060"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s libovolnou <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> kolekcí nebo přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](linq-to-xml.md). LINQ můžete použít k dotazování na všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601> , <xref:System.Array> nebo <xref:System.Collections.Generic.Dictionary%602> . Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.  
  
 V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím. Starým způsobem museli napsat složitou `For Each` smyčku, která určuje, jak načíst data z kolekce. V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `For Each` smyčkám:  
  
1. Jsou stručnější a čitelné, zejména při filtrování více podmínek.  
  
2. Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.  
  
3. Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.  
  
 Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.  
  
 Účelem této části je Ukázat přístup LINQ s některými příklady výběru. Není určena k vyčerpávajícímu určení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (Visual Basic)](linq-and-strings.md)  
 Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců. Obsahuje také odkazy na témata, která ukazují tyto principy.  
  
 [LINQ a reflexe (Visual Basic)](linq-and-reflection.md)  
 Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (Visual Basic)](linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů. Obsahuje také odkazy na témata, která ukazují tyto koncepty.  
  
 [Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak se dotázat na objekt ArrayList v jazyce C#.  
  
 [Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)](how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [LINQ (Language-Integrated Query) (Visual Basic)](index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.

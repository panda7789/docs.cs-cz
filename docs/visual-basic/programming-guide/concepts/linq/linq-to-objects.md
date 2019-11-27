---
title: LINQ na objekty
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354308"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s jakoukoli <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekcí přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Pomocí LINQ můžete zadávat dotazy na všechny vyčíslitelné kolekce, například <xref:System.Collections.Generic.List%601>, <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.  
  
 V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím. Starým způsobem museli napsat komplexní smyčky `For Each`, které určily, jak načíst data z kolekce. V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `For Each` smyčkám:  
  
1. Jsou stručnější a čitelné, zejména při filtrování více podmínek.  
  
2. Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.  
  
3. Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.  
  
 Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.  
  
 Účelem této části je Ukázat přístup LINQ s některými příklady výběru. Není určena k vyčerpávajícímu určení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců. Obsahuje také odkazy na témata, která ukazují tyto principy.  
  
 [LINQ a reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů. Obsahuje také odkazy na témata, která ukazují tyto koncepty.  
  
 [Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak se dotázat na objekt C#ArrayList v.  
  
 [Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [LINQ (Language-Integrated Query) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.

---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: f4ca6e57ffff026cb73121ecaf443ae54b25262c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990019"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)

Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s libovolnou <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> kolekcí nebo přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](./linq-to-xml-overview.md). LINQ můžete použít k dotazování na všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601> , <xref:System.Array> nebo <xref:System.Collections.Generic.Dictionary%602> . Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET API.  
  
 V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím. Starým způsobem museli napsat složitou `foreach` smyčku, která určuje, jak načíst data z kolekce. V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `foreach` smyčkám:  
  
- Jsou stručnější a čitelné, zejména při filtrování více podmínek.  
  
- Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.  
  
- Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.  
  
 Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou použití LINQ namísto tradičních technik iterací.  
  
 Účelem této části je Ukázat přístup LINQ s některými příklady výběru. Není určeno jako vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (C#)](./linq-and-strings.md)  
 Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců. Obsahuje také odkazy na články, které ukazují tyto principy.  
  
 [LINQ a reflexe (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů. Obsahuje také odkazy na články, které ukazují tyto koncepty.  
  
 [Postup dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak se dotázat na objekt ArrayList v jazyce C#.  
  
 [Postup přidání vlastních metod pro dotazy LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.  
  
 [LINQ (Language-Integrated Query) (C#)](./index.md)  
 Obsahuje odkazy na články, které vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.

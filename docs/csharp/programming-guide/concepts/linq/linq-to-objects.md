---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75344785"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s jakoukoli <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekcí přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](./linq-to-xml-overview.md). Pomocí LINQ můžete zadávat dotazy na všechny vyčíslitelné kolekce, například <xref:System.Collections.Generic.List%601>, <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.  
  
 V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím. Starým způsobem museli napsat komplexní smyčky `foreach`, které určily, jak načíst data z kolekce. V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `foreach` smyčkám:  
  
1. Jsou stručnější a čitelné, zejména při filtrování více podmínek.  
  
2. Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.  
  
3. Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.  
  
 Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.  
  
 Účelem této části je Ukázat přístup LINQ s některými příklady výběru. Není určena k vyčerpávajícímu určení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (C#)](./linq-and-strings.md)  
 Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců. Obsahuje také odkazy na témata, která ukazují tyto principy.  
  
 [LINQ a reflexe (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.  
  
 [LINQ a souborové adresáře (C#)](./linq-and-file-directories.md)  
 Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů. Obsahuje také odkazy na témata, která ukazují tyto koncepty.  
  
 [Postup dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak se dotázat na objekt C#ArrayList v.  
  
 [Postup přidání vlastních metod pro dotazy LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [Dotaz integrovaný na jazyku (LINQ)C#()](./index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.

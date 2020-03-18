---
title: LINQ na objekty (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344785"
---
# <a name="linq-to-objects-c"></a>LINQ na objekty (C#)
Termín "LINQ na objekty" odkazuje na použití linq <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> dotazy s any nebo kolekce přímo, bez použití zprostředkovatele zprostředkující LINQ nebo rozhraní API, jako je [LINQ na SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ na XML](./linq-to-xml-overview.md). Linq můžete použít k dotazování libovolných <xref:System.Collections.Generic.List%601>nesčetných kolekcí, jako jsou , <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>. Kolekce může být definována uživatelem nebo může být vrácena rozhraním .NET Framework API.  
  
 V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím. Starým způsobem jste museli napsat `foreach` složité smyčky, které specifikovaly, jak načíst data z kolekce. V přístupu LINQ napíšete deklarativní kód, který popisuje, co chcete načíst.  
  
 Kromě toho linq dotazy nabízejí tři `foreach` hlavní výhody oproti tradičním smyčkám:  
  
1. Jsou stručnější a čitelnější, zejména při filtrování více podmínek.  
  
2. Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.  
  
3. Mohou být přeneseny do jiných zdrojů dat s malou nebo žádnou změnou.  
  
 Obecně platí, že složitější operace, kterou chcete provést s daty, tím větší výhodu získáte pomocí LINQ namísto tradičních iterace.  
  
 Účelem této části je demonstrovat přístup LINQ s některými vybranými příklady. Nemá být vyčerpávající.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [LINQ a řetězce (C#)](./linq-and-strings.md)  
 Vysvětluje, jak LINQ lze použít k dotazování a transformaci řetězce a kolekce řetězců. Obsahuje také odkazy na témata, která tyto zásady demonstrují.  
  
 [LINQ a reflexe (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 Odkazy na ukázku, která ukazuje, jak LINQ používá reflexe.  
  
 [Linq a souborové adresáře (C#)](./linq-and-file-directories.md)  
 Vysvětluje, jak linq lze použít k interakci se systémy souborů. Obsahuje také odkazy na témata, která tyto koncepty demonstrují.  
  
 [Jak dotaz ArrayList s LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)  
 Ukazuje, jak dotaz ArrayList v C#.  
  
 [Jak přidat vlastní metody pro dotazy LINQ (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Vysvětluje, jak rozšířit sadu metod, které můžete použít pro dotazy LINQ <xref:System.Collections.Generic.IEnumerable%601> přidáním metody rozšíření do rozhraní.  
  
 [Dotaz integrovaný jazykem (LINQ) (C#)](./index.md)  
 Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.

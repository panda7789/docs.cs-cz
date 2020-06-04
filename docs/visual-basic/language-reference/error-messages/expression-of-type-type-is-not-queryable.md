---
title: Na výrazy typu <type> nelze zadávat dotazy.
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: e61b4dac109f714b5cf25226d1029237ca77032d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409475"
---
# <a name="expression-of-type-type-is-not-queryable"></a>Na výrazy typu \<type> nelze zadávat dotazy.
Výraz typu není \<type> Queryable. Ujistěte se, že nechybí odkaz na sestavení nebo import oboru názvů pro poskytovatele LINQ.  
  
 Queryable typy jsou definovány v <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> oborech názvů, a. Pro provádění dotazů LINQ musíte importovat jeden nebo více těchto oborů názvů.  
  
 <xref:System.Linq>Obor názvů umožňuje dotazování objektů, jako jsou kolekce a pole pomocí LINQ.  
  
 <xref:System.Data.Linq>Obor názvů umožňuje dotazování ADO.NET datových sad a SQL Server databází pomocí LINQ.  
  
 <xref:System.Xml.Linq>Obor názvů vám umožňuje dotazovat se na XML pomocí LINQ a používat funkce XML v Visual Basic.  
  
 **ID chyby:** BC36593  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přidejte `Import` příkaz pro <xref:System.Linq> <xref:System.Data.Linq> <xref:System.Xml.Linq> obor názvů, nebo do souboru kódu. Obory názvů pro svůj projekt můžete také importovat pomocí stránky **odkazy** Návrháře projektu (**můj projekt**).  
  
2. Ujistěte se, že typ, který jste identifikovali jako zdroj dotazu, je Queryable typ. To znamená, že typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../programming-guide/language-features/linq/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
- [Odkazy a příkaz Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../statements/imports-statement-net-namespace-and-type.md)
- [Stránka Odkazy, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

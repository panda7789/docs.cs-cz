---
title: Na výrazy typu <type> nelze zadávat dotazy.
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 06b2a7f5c6bd838d09fd39f31778462c364fb8bd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261253"
---
# <a name="expression-of-type-type-is-not-queryable"></a>Výraz typu \<typ > není dotazovatelné
Výraz typu \<typ > není zadávat dotazy. Ujistěte se, že nechybí sestavení odkazu nebo import oboru názvů pro zprostředkovatele LINQ.  
  
 Dotazovatelné typy jsou definovány v <xref:System.Linq>, <xref:System.Data.Linq>, a <xref:System.Xml.Linq> obory názvů. Je nutné importovat jeden nebo více z těchto oborů názvů k provádění dotazů LINQ.  
  
 <xref:System.Linq> Obor názvů umožňuje dotazu objekty, jako jsou kolekce a pole s využitím jazyka LINQ.  
  
 <xref:System.Data.Linq> Oborů názvů umožňuje dotazování datovými sadami ADO.NET a databáze systému SQL Server s využitím jazyka LINQ.  
  
 <xref:System.Xml.Linq> Obor názvů umožňuje dotazu XML pomocí LINQ a pokud chcete používat funkce XML v jazyce Visual Basic.  
  
 **ID chyby:** BC36593  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Import` příkaz <xref:System.Linq>, <xref:System.Data.Linq>, nebo <xref:System.Xml.Linq> oboru názvů do souboru kódu. Můžete také importovat obory názvů pro váš projekt s použitím **odkazy** stránky Návrháře projektu (**Můj projekt**).  
  
2.  Ujistěte se, že typ, který jste našli jako dotazovatelný typ je zdroj dotazu. To znamená typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Stránka Odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

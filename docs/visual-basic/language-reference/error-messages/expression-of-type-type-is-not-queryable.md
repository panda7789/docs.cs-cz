---
title: Výraz typu &lt;typ&gt; není dotazovatelné
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 9d333abda5e303f8fab6d1f707df7ac77d8e03ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589006"
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>Výraz typu &lt;typ&gt; není dotazovatelné
Výraz typu \<typ > není dotazovatelnosti. Ujistěte se, že nejsou pro zprostředkovatele LINQ chybí sestavení odkaz nebo obor názvů importu.  
  
 Dotazovatelný typy jsou definované v <xref:System.Linq>, <xref:System.Data.Linq>, a <xref:System.Xml.Linq> obory názvů. Je nutné naimportovat minimálně jeden z těchto oborů názvů provádět dotazy LINQ.  
  
 <xref:System.Linq> Obor názvů umožňuje objekty dotazu, jako jsou kolekce a pole pomocí LINQ.  
  
 <xref:System.Data.Linq> Obor názvů umožňuje ADO.NET datové sady a databáze systému SQL Server pomocí LINQ dotazů.  
  
 <xref:System.Xml.Linq> Obor názvů umožňuje dotazu XML pomocí LINQ a chcete používat funkce XML v jazyce Visual Basic.  
  
 **ID chyby:** BC36593  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přidat `Import` údajů <xref:System.Linq>, <xref:System.Data.Linq>, nebo <xref:System.Xml.Linq> oboru názvů do souboru kódu. Můžete také importovat obory názvů pro váš projekt pomocí **odkazy** stránky v Návrháři projektu (**Můj projekt**).  
  
2.  Zajistěte, aby typ, který jste našli jako zdroj dotazu je typu dotazovatelnosti. To znamená, typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Stránka Odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

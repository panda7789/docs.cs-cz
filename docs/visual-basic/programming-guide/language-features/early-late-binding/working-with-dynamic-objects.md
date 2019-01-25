---
title: Práce s dynamickými objekty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 14bd78f2897edc9f2092e062fda16ba5a7d04c37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640859"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Práce s dynamickými objekty (Visual Basic)
Dynamické objekty poskytují dalším způsobem, jiné než `Object` typ pozdní vazby na objekt v době běhu. Dynamický objekt zveřejňuje členy jako jsou vlastnosti a metody v době běhu pomocí dynamické rozhraní, které jsou definovány v <xref:System.Dynamic> oboru názvů. Můžete použít třídy v <xref:System.Dynamic> obor názvů umožní vytvořit objekty, které pracují s datovými strukturami, které neodpovídají statický typ nebo formát. Můžete také použít dynamické objekty, které jsou definovány v dynamické jazyky, jako je například IronPython a IronRuby. Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v dynamického jazyka naleznete v tématu [názorný postup: Vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, nebo <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic vytvoří vazbu na objekty z dynamickým jazykovým modulem runtime a dynamické jazyky, jako je například IronPython a IronRuby pomocí <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Příklady tříd, které implementují `IDynamicMetaObjectProvider` rozhraní jsou <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject> třídy.  
  
 Pokud je provedeno volání s pozdní vazbou na objekt, který implementuje `IDynamicMetaObjectProvider` rozhraní jazyka Visual Basic vytvoří vazbu na dynamický objekt s použitím rozhraní. Pokud je provedeno volání s pozdní vazbou na objekt, který neimplementuje `IDynamicMetaObjectProvider` rozhraní, nebo pokud volání `IDynamicMetaObjectProvider` rozhraní selže, Visual Basic vytvoří vazbu k objektu pomocí funkce pozdní vazby modulu runtime jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Návod: Vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Statické a dynamické vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)

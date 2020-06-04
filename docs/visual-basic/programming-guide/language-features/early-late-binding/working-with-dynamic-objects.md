---
title: Práce s dynamickými objekty
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 13b7c80537700c934dbb807b0f264218357088ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405167"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Práce s dynamickými objekty (Visual Basic)
Dynamické objekty poskytují jiný způsob, než `Object` typ, k pozdní vazbě na objekt v době běhu. Dynamický objekt zpřístupňuje členy, jako jsou vlastnosti a metody v době běhu, pomocí dynamických rozhraní, která jsou definována v <xref:System.Dynamic> oboru názvů. Třídy v <xref:System.Dynamic> oboru názvů můžete použít k vytvoření objektů, které pracují s datovými strukturami, které neodpovídají statickému typu nebo formátu. Můžete také použít dynamické objekty, které jsou definovány v dynamických jazycích, například Ironpythonu a IronRuby. Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v dynamickém jazyce, naleznete v tématu [Návod: vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject> , nebo <xref:System.Dynamic.ExpandoObject> .  
  
 Visual Basic se váže k objektům z dynamického jazykového modulu runtime a dynamické jazyky, jako je například Ironpythonu a IronRuby, pomocí <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Příklady tříd, které implementují `IDynamicMetaObjectProvider` rozhraní, jsou <xref:System.Dynamic.DynamicObject> <xref:System.Dynamic.ExpandoObject> třídy a.  
  
 Pokud je provedeno volání s pozdní vazbou na objekt, který implementuje `IDynamicMetaObjectProvider` rozhraní, Visual Basic vytvoří vazbu k dynamickému objektu pomocí tohoto rozhraní. Pokud je provedeno volání s pozdní vazbou na objekt, který neimplementuje `IDynamicMetaObjectProvider` rozhraní, nebo pokud volání `IDynamicMetaObjectProvider` rozhraní neproběhne úspěšně, Visual Basic váže k objektu pomocí možností pozdní vazby modulu runtime Visual Basic.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Návod: vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Počáteční a pozdní vazba](index.md)

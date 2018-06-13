---
title: Práce s dynamickými objekty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647346"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Práce s dynamickými objekty (Visual Basic)
Dynamické objekty poskytují jiný způsob, než `Object` typ pozdní vazby k objektu v době běhu. Dynamický objekt zveřejňuje členy například vlastnosti a metody v době běhu pomocí dynamické rozhraní, které jsou definovány v <xref:System.Dynamic> oboru názvů. Můžete použít třídy v <xref:System.Dynamic> oboru názvů k vytváření objektů, které pracují s datové struktury, které neodpovídají statický typ nebo formát. Můžete také použít dynamické objekty, které jsou definovány v dynamické jazyků, například IronPython a IronRuby. Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v jiném jazyce, dynamické najdete v tématu [návod: vytváření a použití dynamické objekty](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, nebo <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic váže na objekty z dynamické běhové prostředí a dynamické jazyků, například IronPython a IronRuby pomocí <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Příklady tříd, které implementují `IDynamicMetaObjectProvider` rozhraní jsou <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject> třídy.  
  
 Pokud na objekt, který implementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní, Visual Basic vazby k objektu dynamické pomocí tohoto rozhraní. Pokud na objekt, který neimplementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní, nebo pokud volání `IDynamicMetaObjectProvider` rozhraní selže, Visual Basic váže k objektu pomocí funkce pozdní vazba modulu runtime jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Návod: Vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Statické a dynamické vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)

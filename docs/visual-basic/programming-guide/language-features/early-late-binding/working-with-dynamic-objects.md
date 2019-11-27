---
title: Práce s dynamickými objekty
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345166"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Práce s dynamickými objekty (Visual Basic)
Dynamické objekty poskytují jiný způsob, jiný než typ `Object`, aby bylo možné pozdní vazby na objekt v době běhu. Dynamický objekt zpřístupňuje členy, jako jsou vlastnosti a metody v době běhu, pomocí dynamických rozhraní, která jsou definována v oboru názvů <xref:System.Dynamic>. Třídy v oboru názvů <xref:System.Dynamic> lze použít k vytvoření objektů, které pracují s datovými strukturami, které neodpovídají statickému typu nebo formátu. Můžete také použít dynamické objekty, které jsou definovány v dynamických jazycích, například Ironpythonu a IronRuby. Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v dynamickém jazyce, naleznete v tématu [Návod: vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>nebo <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic se váže k objektům z dynamického jazykového modulu runtime a dynamické jazyky, jako je například Ironpythonu a IronRuby, pomocí rozhraní <xref:System.Dynamic.IDynamicMetaObjectProvider>. Příklady tříd, které implementují rozhraní `IDynamicMetaObjectProvider`, jsou třídy <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject>.  
  
 Pokud je provedeno volání s pozdní vazbou na objekt, který implementuje rozhraní `IDynamicMetaObjectProvider`, Visual Basic vytvoří vazbu k dynamickému objektu pomocí tohoto rozhraní. Pokud je provedeno volání s pozdní vazbou na objekt, který neimplementuje rozhraní `IDynamicMetaObjectProvider`, nebo pokud se volání rozhraní `IDynamicMetaObjectProvider` nepovede, Visual Basic se sváže s objektem pomocí možností pozdní vazby modulu runtime Visual Basic.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Návod: vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Statické a pozdní vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)

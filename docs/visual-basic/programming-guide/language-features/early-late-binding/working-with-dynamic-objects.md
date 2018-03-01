---
title: "Práce s dynamickými objekty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Práce s dynamickými objekty (Visual Basic)
Dynamické objekty poskytují jiný způsob, než `Object` typ pozdní vazby k objektu v době běhu. Dynamický objekt zveřejňuje členy například vlastnosti a metody v době běhu pomocí dynamické rozhraní, které jsou definovány v <xref:System.Dynamic> oboru názvů. Můžete použít třídy v <xref:System.Dynamic> oboru názvů k vytváření objektů, které pracují s datové struktury, které neodpovídají statický typ nebo formát. Můžete také použít dynamické objekty, které jsou definovány v dynamické jazyků, například IronPython a IronRuby. Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v jiném jazyce, dynamické najdete v tématu [návod: vytváření a použití dynamické objekty](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, nebo <xref:System.Dynamic.ExpandoObject>.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]vytvoří vazbu objekty z dynamické běhové prostředí a dynamické jazyků, například IronPython a IronRuby pomocí <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Příklady tříd, které implementují `IDynamicMetaObjectProvider` rozhraní jsou <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject> třídy.  
  
 Pokud na objekt, který implementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] váže k dynamických objektů pomocí tohoto rozhraní. Pokud na objekt, který neimplementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní, nebo, pokud volání `IDynamicMetaObjectProvider` rozhraní selže, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] váže k objektu pomocí funkce pozdní vazba [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modulu runtime.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Návod: Vytváření a používání dynamických objektů](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Statické a pozdní vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)

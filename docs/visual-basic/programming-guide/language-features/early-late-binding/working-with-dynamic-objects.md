---
title: Práce s dynamickými objekty (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f00c57107da5e6ea428e14964d8fa4a870bc96c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="74aca-102">Práce s dynamickými objekty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74aca-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="74aca-103">Dynamické objekty poskytují jiný způsob, než `Object` typ pozdní vazby k objektu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="74aca-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="74aca-104">Dynamický objekt zveřejňuje členy například vlastnosti a metody v době běhu pomocí dynamické rozhraní, které jsou definovány v <xref:System.Dynamic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74aca-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="74aca-105">Můžete použít třídy v <xref:System.Dynamic> oboru názvů k vytváření objektů, které pracují s datové struktury, které neodpovídají statický typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="74aca-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="74aca-106">Můžete také použít dynamické objekty, které jsou definovány v dynamické jazyků, například IronPython a IronRuby.</span><span class="sxs-lookup"><span data-stu-id="74aca-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="74aca-107">Příklady, které ukazují, jak vytvořit dynamické objekty nebo použít dynamický objekt definovaný v jiném jazyce, dynamické najdete v tématu [návod: vytváření a použití dynamické objekty](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, nebo <xref:System.Dynamic.ExpandoObject>.</span><span class="sxs-lookup"><span data-stu-id="74aca-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="74aca-108">Visual Basic váže na objekty z dynamické běhové prostředí a dynamické jazyků, například IronPython a IronRuby pomocí <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74aca-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="74aca-109">Příklady tříd, které implementují `IDynamicMetaObjectProvider` rozhraní jsou <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject> třídy.</span><span class="sxs-lookup"><span data-stu-id="74aca-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="74aca-110">Pokud na objekt, který implementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní, Visual Basic vazby k objektu dynamické pomocí tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74aca-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="74aca-111">Pokud na objekt, který neimplementuje Přišla žádost o pozdní vazbou `IDynamicMetaObjectProvider` rozhraní, nebo pokud volání `IDynamicMetaObjectProvider` rozhraní selže, Visual Basic váže k objektu pomocí funkce pozdní vazba modulu runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="74aca-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74aca-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="74aca-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="74aca-113">Návod: Vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="74aca-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="74aca-114">Statické a dynamické vazby</span><span class="sxs-lookup"><span data-stu-id="74aca-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)

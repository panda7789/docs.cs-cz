---
title: "GetType – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="b43cc-102">GetType – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b43cc-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="b43cc-103">Vrátí <xref:System.Type> objekt pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="b43cc-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="b43cc-104"><xref:System.Type> Objekt poskytuje informace o typu, například jeho vlastnosti, metod a události.</span><span class="sxs-lookup"><span data-stu-id="b43cc-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b43cc-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b43cc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b43cc-106">Parameters</span></span>  
  
|<span data-ttu-id="b43cc-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="b43cc-107">Parameter</span></span>|<span data-ttu-id="b43cc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b43cc-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="b43cc-109">Název typu, pro které očekáváte informace.</span><span class="sxs-lookup"><span data-stu-id="b43cc-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b43cc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b43cc-110">Remarks</span></span>  
 <span data-ttu-id="b43cc-111">`GetType` Vrátí operátor <xref:System.Type> objekt pro zadaný `typename`.</span><span class="sxs-lookup"><span data-stu-id="b43cc-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="b43cc-112">Můžete předat název typu žádné definované v `typename`.</span><span class="sxs-lookup"><span data-stu-id="b43cc-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="b43cc-113">To zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="b43cc-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="b43cc-114">Zadejte všechna data jazyka Visual Basic, například `Boolean` nebo `Date`.</span><span class="sxs-lookup"><span data-stu-id="b43cc-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="b43cc-115">Všechny třídy rozhraní .NET Framework, struktury, modul nebo rozhraní, jako například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b43cc-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="b43cc-116">Všechny třídy, struktury, modul nebo rozhraní definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="b43cc-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="b43cc-117">Žádné pole definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="b43cc-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="b43cc-118">Všechny delegát definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="b43cc-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="b43cc-119">Všechny výčtu definované jazyka Visual Basic, rozhraní .NET Framework nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="b43cc-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="b43cc-120">Pokud chcete získat objekt typu objektové proměnné, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b43cc-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b43cc-121">`GetType` Operátor může být užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="b43cc-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="b43cc-122">Metadata pro typ potřebuje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="b43cc-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="b43cc-123"><xref:System.Type> Objekt poskytuje metadata například členy typu a informace o nasazení.</span><span class="sxs-lookup"><span data-stu-id="b43cc-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="b43cc-124">Potřebujete, například tak, aby odrážela přes sestavení.</span><span class="sxs-lookup"><span data-stu-id="b43cc-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="b43cc-125">Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b43cc-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="b43cc-126">Chcete porovnat dva odkazy na objekty zobrazíte Pokud odkazují instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b43cc-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="b43cc-127">Pokud tomu tak je, `GetType` vrátí odkazy na stejné <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="b43cc-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b43cc-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="b43cc-128">Example</span></span>  
 <span data-ttu-id="b43cc-129">Následující příklady zobrazují `GetType` operátor používá.</span><span class="sxs-lookup"><span data-stu-id="b43cc-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b43cc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b43cc-130">See Also</span></span>  
 [<span data-ttu-id="b43cc-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b43cc-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b43cc-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b43cc-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b43cc-133">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="b43cc-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

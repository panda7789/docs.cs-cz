---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603844"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="659a6-102">GetType – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="659a6-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="659a6-103">Vrátí <xref:System.Type> objekt pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="659a6-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="659a6-104"><xref:System.Type> Objekt poskytuje informace o typu, například jeho vlastnosti, metod a události.</span><span class="sxs-lookup"><span data-stu-id="659a6-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="659a6-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="659a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="659a6-106">Parameters</span></span>  
  
|<span data-ttu-id="659a6-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="659a6-107">Parameter</span></span>|<span data-ttu-id="659a6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="659a6-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="659a6-109">Název typu, pro které očekáváte informace.</span><span class="sxs-lookup"><span data-stu-id="659a6-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="659a6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="659a6-110">Remarks</span></span>  
 <span data-ttu-id="659a6-111">`GetType` Vrátí operátor <xref:System.Type> objekt pro zadaný `typename`.</span><span class="sxs-lookup"><span data-stu-id="659a6-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="659a6-112">Můžete předat název typu žádné definované v `typename`.</span><span class="sxs-lookup"><span data-stu-id="659a6-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="659a6-113">To zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="659a6-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="659a6-114">Zadejte všechna data jazyka Visual Basic, například `Boolean` nebo `Date`.</span><span class="sxs-lookup"><span data-stu-id="659a6-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="659a6-115">Všechny třídy rozhraní .NET Framework, struktury, modul nebo rozhraní, jako například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="659a6-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="659a6-116">Všechny třídy, struktury, modul nebo rozhraní definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="659a6-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="659a6-117">Žádné pole definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="659a6-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="659a6-118">Všechny delegát definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="659a6-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="659a6-119">Všechny výčtu definované jazyka Visual Basic, rozhraní .NET Framework nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="659a6-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="659a6-120">Pokud chcete získat objekt typu objektové proměnné, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="659a6-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="659a6-121">`GetType` Operátor může být užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="659a6-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="659a6-122">Metadata pro typ potřebuje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="659a6-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="659a6-123"><xref:System.Type> Objekt poskytuje metadata například členy typu a informace o nasazení.</span><span class="sxs-lookup"><span data-stu-id="659a6-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="659a6-124">Potřebujete, například tak, aby odrážela přes sestavení.</span><span class="sxs-lookup"><span data-stu-id="659a6-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="659a6-125">Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="659a6-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="659a6-126">Chcete porovnat dva odkazy na objekty zobrazíte Pokud odkazují instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="659a6-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="659a6-127">Pokud tomu tak je, `GetType` vrátí odkazy na stejné <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="659a6-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="659a6-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="659a6-128">Example</span></span>  
 <span data-ttu-id="659a6-129">Následující příklady zobrazují `GetType` operátor používá.</span><span class="sxs-lookup"><span data-stu-id="659a6-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="659a6-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="659a6-130">See Also</span></span>  
 [<span data-ttu-id="659a6-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="659a6-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="659a6-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="659a6-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="659a6-133">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="659a6-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

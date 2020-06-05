---
title: GetType – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 37644a9c37ffde084120c5f1e1ee8c87a04ffc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371152"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="f7788-102">GetType – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7788-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="f7788-103">Vrátí <xref:System.Type> objekt pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="f7788-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="f7788-104"><xref:System.Type>Objekt poskytuje informace o typu, jako jsou vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="f7788-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7788-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7788-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7788-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7788-106">Parameters</span></span>  
  
|<span data-ttu-id="f7788-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="f7788-107">Parameter</span></span>|<span data-ttu-id="f7788-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f7788-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="f7788-109">Název typu, pro který si přejete získat informace.</span><span class="sxs-lookup"><span data-stu-id="f7788-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7788-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7788-110">Remarks</span></span>  
 <span data-ttu-id="f7788-111">`GetType`Operátor vrátí <xref:System.Type> objekt pro zadanou hodnotu `typename` .</span><span class="sxs-lookup"><span data-stu-id="f7788-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="f7788-112">Můžete předat název libovolného definovaného typu v `typename` .</span><span class="sxs-lookup"><span data-stu-id="f7788-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="f7788-113">Ta zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="f7788-113">This includes the following:</span></span>  
  
- <span data-ttu-id="f7788-114">Libovolný datový typ Visual Basic, například `Boolean` nebo `Date` .</span><span class="sxs-lookup"><span data-stu-id="f7788-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="f7788-115">Jakékoli .NET Framework třídy, struktury, modulu nebo rozhraní, například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f7788-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f7788-116">Libovolná třída, struktura, modul nebo rozhraní definované vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f7788-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="f7788-117">Jakékoli pole definované vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f7788-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="f7788-118">Libovolný delegát definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f7788-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="f7788-119">Jakýkoli výčet definovaný Visual Basic, .NET Framework nebo vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f7788-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="f7788-120">Pokud chcete získat objekt typu proměnné objektu, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="f7788-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f7788-121">`GetType`Operátor může být užitečný v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="f7788-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="f7788-122">Je nutné přístup k metadatům pro typ v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f7788-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="f7788-123"><xref:System.Type>Objekt poskytuje metadata jako členy typu a informace o nasazení.</span><span class="sxs-lookup"><span data-stu-id="f7788-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="f7788-124">Potřebujete například, aby odrážely sestavení.</span><span class="sxs-lookup"><span data-stu-id="f7788-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="f7788-125">Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7788-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f7788-126">Chcete porovnat dva odkazy na objekty, abyste viděli, zda odkazují na instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f7788-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="f7788-127">Pokud jsou, `GetType` vrátí odkazy na stejný <xref:System.Type> objekt.</span><span class="sxs-lookup"><span data-stu-id="f7788-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7788-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7788-128">Example</span></span>  
 <span data-ttu-id="f7788-129">Následující příklady znázorňují operátor, který se `GetType` používá.</span><span class="sxs-lookup"><span data-stu-id="f7788-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="f7788-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7788-130">See also</span></span>

- [<span data-ttu-id="f7788-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7788-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f7788-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f7788-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f7788-133">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="f7788-133">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)

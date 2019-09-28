---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592155"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="0d0c2-102">GetType – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d0c2-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="0d0c2-103">Vrátí objekt <xref:System.Type> pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="0d0c2-104">Objekt <xref:System.Type> poskytuje informace o typu, jako jsou vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d0c2-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d0c2-106">Parameters</span></span>  
  
|<span data-ttu-id="0d0c2-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="0d0c2-107">Parameter</span></span>|<span data-ttu-id="0d0c2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0d0c2-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="0d0c2-109">Název typu, pro který si přejete získat informace.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d0c2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d0c2-110">Remarks</span></span>  
 <span data-ttu-id="0d0c2-111">Operátor `GetType` vrátí objekt <xref:System.Type> pro zadaný `typename`.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="0d0c2-112">Název libovolného definovaného typu můžete předat `typename`.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="0d0c2-113">Ta zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="0d0c2-113">This includes the following:</span></span>  
  
- <span data-ttu-id="0d0c2-114">Libovolný datový typ Visual Basic, například `Boolean` nebo `Date`.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="0d0c2-115">Jakékoli .NET Framework třídy, struktury, modulu nebo rozhraní, například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="0d0c2-116">Libovolná třída, struktura, modul nebo rozhraní definované vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="0d0c2-117">Jakékoli pole definované vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="0d0c2-118">Libovolný delegát definovaný vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="0d0c2-119">Jakýkoli výčet definovaný Visual Basic, .NET Framework nebo vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="0d0c2-120">Pokud chcete získat objekt typu proměnné objektu, použijte metodu <xref:System.Type.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0d0c2-121">Operátor `GetType` může být užitečný v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="0d0c2-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="0d0c2-122">Je nutné přístup k metadatům pro typ v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="0d0c2-123">Objekt <xref:System.Type> poskytuje metadata jako členy typu a informace o nasazení.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="0d0c2-124">Potřebujete například, aby odrážely sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="0d0c2-125">Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="0d0c2-126">Chcete porovnat dva odkazy na objekty, abyste viděli, zda odkazují na instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="0d0c2-127">Pokud tomu tak je, `GetType` vrátí odkazy na stejný objekt <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0c2-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d0c2-128">Example</span></span>  
 <span data-ttu-id="0d0c2-129">Následující příklady znázorňují operátor `GetType`, který se používá.</span><span class="sxs-lookup"><span data-stu-id="0d0c2-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="0d0c2-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d0c2-130">See also</span></span>

- [<span data-ttu-id="0d0c2-131">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d0c2-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0d0c2-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0d0c2-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0d0c2-133">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="0d0c2-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

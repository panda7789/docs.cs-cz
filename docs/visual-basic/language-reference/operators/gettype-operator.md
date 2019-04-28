---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 34ab192814583db5cdc0d0183c73cc22b8633e9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663606"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="a79df-102">GetType – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a79df-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="a79df-103">Vrátí <xref:System.Type> objekt zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="a79df-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="a79df-104"><xref:System.Type> Objekt poskytuje informace o typu jako jeho vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="a79df-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a79df-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a79df-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="a79df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a79df-106">Parameters</span></span>  
  
|<span data-ttu-id="a79df-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="a79df-107">Parameter</span></span>|<span data-ttu-id="a79df-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a79df-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="a79df-109">Název typu, pro kterou vyžadujete informace.</span><span class="sxs-lookup"><span data-stu-id="a79df-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a79df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a79df-110">Remarks</span></span>  
 <span data-ttu-id="a79df-111">`GetType` Operátor vrátí <xref:System.Type> objekt pro zadaný rozbočovač `typename`.</span><span class="sxs-lookup"><span data-stu-id="a79df-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="a79df-112">Můžete předat název libovolného typu definované v `typename`.</span><span class="sxs-lookup"><span data-stu-id="a79df-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="a79df-113">Ta zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="a79df-113">This includes the following:</span></span>  
  
- <span data-ttu-id="a79df-114">Zadejte všechna data v jazyce Visual Basic, například `Boolean` nebo `Date`.</span><span class="sxs-lookup"><span data-stu-id="a79df-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="a79df-115">Všechny třídy rozhraní .NET Framework, struktura, modul nebo rozhraní, jako například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a79df-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="a79df-116">Všechny třídy, struktury, modul nebo rozhraní definovaných v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a79df-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="a79df-117">Jakékoli pole definovaných v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a79df-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="a79df-118">Jakýkoli delegát definovaných v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a79df-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="a79df-119">Žádné výčtu definované jazyka Visual Basic, rozhraní .NET Framework nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="a79df-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="a79df-120">Pokud chcete získat objekt typu objektové proměnné, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a79df-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a79df-121">`GetType` Operátor může být užitečná v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a79df-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="a79df-122">Třeba získat přístup k metadatům pro typ v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a79df-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="a79df-123"><xref:System.Type> Objekt poskytuje metadat – například členy typu a informace o nasazení.</span><span class="sxs-lookup"><span data-stu-id="a79df-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="a79df-124">Je třeba to, například reflexi pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a79df-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="a79df-125">Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a79df-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="a79df-126">Chcete porovnat dva odkazy na objekty a zjistěte, jestli se vztahují na instance stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a79df-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="a79df-127">V takovém případě `GetType` vrátí odkazy na stejný <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="a79df-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a79df-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="a79df-128">Example</span></span>  
 <span data-ttu-id="a79df-129">Následující příklady ukazují `GetType` operátor používá.</span><span class="sxs-lookup"><span data-stu-id="a79df-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="a79df-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79df-130">See also</span></span>

- [<span data-ttu-id="a79df-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a79df-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a79df-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a79df-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a79df-133">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="a79df-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

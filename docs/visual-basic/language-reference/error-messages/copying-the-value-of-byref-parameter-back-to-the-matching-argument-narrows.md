---
title: "Kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument narrows z typu & č. 39;&lt; NázevTypu1&gt;& č. 39; na typ & č. 39;&lt; NázevTypu2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="7d27c-102">Kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument narrows z typu & č. 39;&lt; NázevTypu1&gt;& č. 39; na typ & č. 39;&lt; NázevTypu2&gt;& č. 39;</span><span class="sxs-lookup"><span data-stu-id="7d27c-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="7d27c-103">Postup je volána s argumentem, která rozšiřuje na s typem parametru odpovídající a je zužující převod parametr argument.</span><span class="sxs-lookup"><span data-stu-id="7d27c-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="7d27c-104">Když definujete třídu nebo strukturu, můžete definovat jeden nebo více operátorů převodu typu třídu nebo strukturu převést na jiné typy.</span><span class="sxs-lookup"><span data-stu-id="7d27c-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="7d27c-105">Můžete také definovat zpětný převod operátory převést tyto typy zpět do vaší třídy nebo typ struktury.</span><span class="sxs-lookup"><span data-stu-id="7d27c-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="7d27c-106">Pokud použijete typ vašeho třídu nebo strukturu ve volání procedury, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] můžete použít tyto operátory převodu typu argument převést na typ jeho odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="7d27c-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="7d27c-107">Pokud předáte argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] někdy zkopíruje hodnota argumentu do místní proměnné v postupu neprochází odkaz.</span><span class="sxs-lookup"><span data-stu-id="7d27c-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="7d27c-108">V takovém případě, když se proces vrátí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zpět do argument ve volání kód musí zkopírujte místní hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="7d27c-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="7d27c-109">Pokud `ByRef` hodnota argumentu se zkopíruje do procesu a argumentů a parametrů jsou stejného typu, je nutné žádný převod.</span><span class="sxs-lookup"><span data-stu-id="7d27c-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="7d27c-110">Pokud se typy liší, ale [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nutné převést v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="7d27c-110">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="7d27c-111">Pokud jeden z typů třídu nebo strukturu typu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musí ho převést na a z jiných typu.</span><span class="sxs-lookup"><span data-stu-id="7d27c-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="7d27c-112">Pokud jeden z těchto převody je rozšíření, může být zužující zpětný převod.</span><span class="sxs-lookup"><span data-stu-id="7d27c-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="7d27c-113">**ID chyby:** BC32053</span><span class="sxs-lookup"><span data-stu-id="7d27c-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d27c-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7d27c-114">To correct this error</span></span>  
  
-   <span data-ttu-id="7d27c-115">Pokud je to možné, použijte volání argument stejného typu jako parametr postupu, takže [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] není nutné provádět jakékoli převody.</span><span class="sxs-lookup"><span data-stu-id="7d27c-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="7d27c-116">Pokud potřebujete volání procedury s argumentem, zadejte odlišný od typu parametru ale nemusíte vrátit hodnotu do volání argument, definujte parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="7d27c-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="7d27c-117">Pokud budete potřebovat vrátit hodnotu do volání argument, definice operátora zpětný převod jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="7d27c-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d27c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d27c-118">See Also</span></span>  
 [<span data-ttu-id="7d27c-119">Postupy</span><span class="sxs-lookup"><span data-stu-id="7d27c-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="7d27c-120">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="7d27c-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="7d27c-121">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="7d27c-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="7d27c-122">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="7d27c-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="7d27c-123">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="7d27c-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="7d27c-124">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="7d27c-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="7d27c-125">Postupy: definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="7d27c-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="7d27c-126">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d27c-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="7d27c-127">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="7d27c-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

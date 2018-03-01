---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="a90bb-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a90bb-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="a90bb-103">Určuje, že proměnné nebo vlastnosti lze číst, ale nebyl zapsán.</span><span class="sxs-lookup"><span data-stu-id="a90bb-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a90bb-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a90bb-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a90bb-105">Pravidla</span><span class="sxs-lookup"><span data-stu-id="a90bb-105">Rules</span></span>  
  
-   <span data-ttu-id="a90bb-106">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="a90bb-106">**Declaration Context.**</span></span> <span data-ttu-id="a90bb-107">Můžete použít `ReadOnly` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="a90bb-108">To znamená kontext deklarace `ReadOnly` element musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="a90bb-109">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="a90bb-109">**Combined Modifiers.**</span></span> <span data-ttu-id="a90bb-110">Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="a90bb-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="a90bb-111">**Přiřazení hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="a90bb-111">**Assigning a Value.**</span></span> <span data-ttu-id="a90bb-112">Použití kódu `ReadOnly` vlastnost nelze nastavit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="a90bb-113">Ale kód, který má přístup k podkladové úložiště přiřadit, nebo změňte hodnotu kdykoli.</span><span class="sxs-lookup"><span data-stu-id="a90bb-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="a90bb-114">Můžete přiřadit hodnotu na `ReadOnly` proměnné pouze v jeho deklaraci nebo v konstruktoru třídu nebo strukturu, ve kterém je definovaný.</span><span class="sxs-lookup"><span data-stu-id="a90bb-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="a90bb-115">Kdy použít proměnnou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a90bb-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="a90bb-116">Existují situace, ve kterých se nedá použít [příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md) deklarovat a přiřadit konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="a90bb-117">Například `Const` příkaz nemusí přijmout datový typ chcete přiřadit, nebo není možné k výpočtu hodnoty v době kompilace s konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="a90bb-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="a90bb-118">Hodnota nemusí vědět i v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a90bb-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="a90bb-119">V těchto případech můžete použít `ReadOnly` proměnnou pro uložení konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a90bb-120">Pokud datový typ proměnné je odkazového typu, jako je například pole nebo instance třídy, i když je proměnná samotné lze změnit její členy `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="a90bb-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="a90bb-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a90bb-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="a90bb-122">Při inicializaci, pole na kterou odkazuje `characterArray()` blokování "x", "y" a "z".</span><span class="sxs-lookup"><span data-stu-id="a90bb-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="a90bb-123">Protože proměnnou `characterArray` je `ReadOnly`, jeho hodnotu nelze změnit po inicializaci; je, není možné přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="a90bb-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="a90bb-124">Můžete však změnit hodnoty jednoho nebo více členů pole.</span><span class="sxs-lookup"><span data-stu-id="a90bb-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="a90bb-125">Po výzvě k postupu `changeArrayElement`, pole na kterou odkazuje `characterArray()` blokování "x", "M" a "z".</span><span class="sxs-lookup"><span data-stu-id="a90bb-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="a90bb-126">Tento název se podobně jako deklarace parametru procedury být [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což zabraňuje měnit volání samotného argumentu postup, ale umožní změnit její členy.</span><span class="sxs-lookup"><span data-stu-id="a90bb-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a90bb-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="a90bb-127">Example</span></span>  
 <span data-ttu-id="a90bb-128">V následujícím příkladu definuje `ReadOnly` vlastnost pro datum přijetí zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="a90bb-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="a90bb-129">Třída úložiště vlastnost hodnota interně jako `Private` kód proměnnou a to pouze uvnitř třídy můžete změnit tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a90bb-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="a90bb-130">Je však vlastnost `Public`, a kód, který může přistupovat k třídě může číst vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a90bb-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="a90bb-131">`ReadOnly` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="a90bb-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a90bb-132">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="a90bb-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="a90bb-133">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="a90bb-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a90bb-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a90bb-134">See Also</span></span>  
 [<span data-ttu-id="a90bb-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="a90bb-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="a90bb-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a90bb-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

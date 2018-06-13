---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599909"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="c4d27-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4d27-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="c4d27-103">Určuje, že proměnné nebo vlastnosti lze číst, ale nebyl zapsán.</span><span class="sxs-lookup"><span data-stu-id="c4d27-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4d27-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4d27-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c4d27-105">Pravidla</span><span class="sxs-lookup"><span data-stu-id="c4d27-105">Rules</span></span>  
  
-   <span data-ttu-id="c4d27-106">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="c4d27-106">**Declaration Context.**</span></span> <span data-ttu-id="c4d27-107">Můžete použít `ReadOnly` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="c4d27-108">To znamená kontext deklarace `ReadOnly` element musí být třída, struktura nebo modul a nemůže být zdrojový soubor, obor názvů nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="c4d27-109">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="c4d27-109">**Combined Modifiers.**</span></span> <span data-ttu-id="c4d27-110">Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c4d27-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="c4d27-111">**Přiřazení hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="c4d27-111">**Assigning a Value.**</span></span> <span data-ttu-id="c4d27-112">Použití kódu `ReadOnly` vlastnost nelze nastavit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="c4d27-113">Ale kód, který má přístup k podkladové úložiště přiřadit, nebo změňte hodnotu kdykoli.</span><span class="sxs-lookup"><span data-stu-id="c4d27-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="c4d27-114">Můžete přiřadit hodnotu na `ReadOnly` proměnné pouze v jeho deklaraci nebo v konstruktoru třídu nebo strukturu, ve kterém je definovaný.</span><span class="sxs-lookup"><span data-stu-id="c4d27-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="c4d27-115">Kdy použít proměnnou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c4d27-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="c4d27-116">Existují situace, ve kterých se nedá použít [příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md) deklarovat a přiřadit konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="c4d27-117">Například `Const` příkaz nemusí přijmout datový typ chcete přiřadit, nebo není možné k výpočtu hodnoty v době kompilace s konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="c4d27-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="c4d27-118">Hodnota nemusí vědět i v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c4d27-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="c4d27-119">V těchto případech můžete použít `ReadOnly` proměnnou pro uložení konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4d27-120">Pokud datový typ proměnné je odkazového typu, jako je například pole nebo instance třídy, i když je proměnná samotné lze změnit její členy `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="c4d27-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="c4d27-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c4d27-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="c4d27-122">Při inicializaci, pole na kterou odkazuje `characterArray()` blokování "x", "y" a "z".</span><span class="sxs-lookup"><span data-stu-id="c4d27-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="c4d27-123">Protože proměnnou `characterArray` je `ReadOnly`, jeho hodnotu nelze změnit po inicializaci; je, není možné přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="c4d27-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="c4d27-124">Můžete však změnit hodnoty jednoho nebo více členů pole.</span><span class="sxs-lookup"><span data-stu-id="c4d27-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="c4d27-125">Po výzvě k postupu `changeArrayElement`, pole na kterou odkazuje `characterArray()` blokování "x", "M" a "z".</span><span class="sxs-lookup"><span data-stu-id="c4d27-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="c4d27-126">Tento název se podobně jako deklarace parametru procedury být [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což zabraňuje měnit volání samotného argumentu postup, ale umožní změnit její členy.</span><span class="sxs-lookup"><span data-stu-id="c4d27-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d27-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4d27-127">Example</span></span>  
 <span data-ttu-id="c4d27-128">V následujícím příkladu definuje `ReadOnly` vlastnost pro datum přijetí zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="c4d27-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="c4d27-129">Třída úložiště vlastnost hodnota interně jako `Private` kód proměnnou a to pouze uvnitř třídy můžete změnit tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4d27-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="c4d27-130">Je však vlastnost `Public`, a kód, který může přistupovat k třídě může číst vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4d27-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="c4d27-131">`ReadOnly` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="c4d27-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c4d27-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="c4d27-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c4d27-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="c4d27-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4d27-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4d27-134">See Also</span></span>  
 [<span data-ttu-id="c4d27-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c4d27-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="c4d27-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c4d27-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

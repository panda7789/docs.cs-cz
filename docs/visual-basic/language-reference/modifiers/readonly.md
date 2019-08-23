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
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965424"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="c281a-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c281a-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="c281a-103">Určuje, že proměnnou nebo vlastnost lze číst, ale nikoli zapsat.</span><span class="sxs-lookup"><span data-stu-id="c281a-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c281a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c281a-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c281a-105">Pravidly</span><span class="sxs-lookup"><span data-stu-id="c281a-105">Rules</span></span>  
  
- <span data-ttu-id="c281a-106">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="c281a-106">**Declaration Context.**</span></span> <span data-ttu-id="c281a-107">Můžete použít `ReadOnly` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="c281a-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="c281a-108">To znamená, že kontext deklarace pro `ReadOnly` prvek musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="c281a-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="c281a-109">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="c281a-109">**Combined Modifiers.**</span></span> <span data-ttu-id="c281a-110">Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c281a-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="c281a-111">**Přiřazení hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="c281a-111">**Assigning a Value.**</span></span> <span data-ttu-id="c281a-112">Kód, který `ReadOnly` spotřebovává vlastnost, nemůže nastavit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c281a-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="c281a-113">Kód, který má přístup k základnímu úložišti, ale může hodnotu kdykoli přiřadit nebo změnit.</span><span class="sxs-lookup"><span data-stu-id="c281a-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="c281a-114">Můžete přiřadit hodnotu `ReadOnly` proměnné pouze v deklaraci nebo v konstruktoru třídy nebo struktury, ve které je definována.</span><span class="sxs-lookup"><span data-stu-id="c281a-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="c281a-115">Kdy použít proměnnou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c281a-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="c281a-116">Existují situace, kdy nelze použít [příkaz const](../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c281a-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="c281a-117">Například `Const` příkaz nemusí přijmout datový typ, který chcete přiřadit, nebo možná nebudete moci vypočítat hodnotu v době kompilace pomocí konstantního výrazu.</span><span class="sxs-lookup"><span data-stu-id="c281a-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="c281a-118">Nemusíte ani znát hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c281a-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="c281a-119">V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c281a-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c281a-120">Pokud je datovým typem proměnné odkazový typ, jako je například pole nebo instance třídy, mohou být jeho členové změněny i v případě, že je `ReadOnly`proměnná sama.</span><span class="sxs-lookup"><span data-stu-id="c281a-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="c281a-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c281a-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="c281a-122">Při inicializaci pole, na `characterArray()` které ukazuje, obsahuje "x", "y" a "z".</span><span class="sxs-lookup"><span data-stu-id="c281a-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="c281a-123">Vzhledem k tomu `characterArray` , `ReadOnly`že proměnná je, nelze po inicializaci změnit její hodnotu; to znamená, že k ní nelze přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="c281a-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="c281a-124">Můžete však změnit hodnoty jednoho nebo více členů pole.</span><span class="sxs-lookup"><span data-stu-id="c281a-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="c281a-125">Po volání procedury `changeArrayElement`se pole, `characterArray()` na které se odkazuje, drží "x", "M" a "z".</span><span class="sxs-lookup"><span data-stu-id="c281a-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="c281a-126">Všimněte si, že je to podobné jako deklarace parametru procedury pro [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což brání postupu v změně samotného argumentu volání, ale umožňuje změnit jeho členy.</span><span class="sxs-lookup"><span data-stu-id="c281a-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c281a-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="c281a-127">Example</span></span>  
 <span data-ttu-id="c281a-128">Následující příklad definuje `ReadOnly` vlastnost pro datum, kdy byl zaměstnanec přijat.</span><span class="sxs-lookup"><span data-stu-id="c281a-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="c281a-129">Třída ukládá hodnotu vlastnosti interně jako `Private` proměnnou a pouze kód uvnitř třídy může tuto hodnotu změnit.</span><span class="sxs-lookup"><span data-stu-id="c281a-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="c281a-130">Vlastnost je `Public`však a jakýkoli kód, který má přístup ke třídě, může číst vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c281a-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c281a-131">V těchto kontextech lze použít Modifikátor:`ReadOnly`</span><span class="sxs-lookup"><span data-stu-id="c281a-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c281a-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="c281a-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c281a-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="c281a-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c281a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c281a-134">See also</span></span>

- [<span data-ttu-id="c281a-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c281a-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="c281a-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c281a-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

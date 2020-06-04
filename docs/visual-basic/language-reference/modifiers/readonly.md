---
title: ReadOnly
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
ms.openlocfilehash: 405297a25d4b948a6920bd989c7826e8b6f66bb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398204"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="4db7d-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4db7d-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="4db7d-103">Určuje, že proměnnou nebo vlastnost lze číst, ale nikoli zapsat.</span><span class="sxs-lookup"><span data-stu-id="4db7d-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="4db7d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4db7d-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="4db7d-105">Pravidla</span><span class="sxs-lookup"><span data-stu-id="4db7d-105">Rules</span></span>

- <span data-ttu-id="4db7d-106">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="4db7d-106">**Declaration Context.**</span></span> <span data-ttu-id="4db7d-107">Můžete použít `ReadOnly` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="4db7d-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="4db7d-108">To znamená, že kontext deklarace pro `ReadOnly` prvek musí být třída, struktura nebo modul a nemůže se jednat o zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="4db7d-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="4db7d-109">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="4db7d-109">**Combined Modifiers.**</span></span> <span data-ttu-id="4db7d-110">Nelze zadat `ReadOnly` společně s `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4db7d-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="4db7d-111">**Přiřazení hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="4db7d-111">**Assigning a Value.**</span></span> <span data-ttu-id="4db7d-112">Kód, který spotřebovává `ReadOnly` vlastnost, nemůže nastavit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4db7d-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="4db7d-113">Kód, který má přístup k základnímu úložišti, ale může hodnotu kdykoli přiřadit nebo změnit.</span><span class="sxs-lookup"><span data-stu-id="4db7d-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="4db7d-114">Můžete přiřadit hodnotu `ReadOnly` proměnné pouze v deklaraci nebo v konstruktoru třídy nebo struktury, ve které je definována.</span><span class="sxs-lookup"><span data-stu-id="4db7d-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="4db7d-115">Kdy použít proměnnou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4db7d-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="4db7d-116">Existují situace, kdy nelze použít [příkaz const](../statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4db7d-116">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="4db7d-117">Například `Const` příkaz nemusí přijmout datový typ, který chcete přiřadit, nebo možná nebudete moci vypočítat hodnotu v době kompilace pomocí konstantního výrazu.</span><span class="sxs-lookup"><span data-stu-id="4db7d-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="4db7d-118">Nemusíte ani znát hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4db7d-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="4db7d-119">V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4db7d-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4db7d-120">Pokud je datovým typem proměnné odkazový typ, jako je například pole nebo instance třídy, mohou být jeho členové změněny i v případě, že je proměnná sama `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="4db7d-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="4db7d-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4db7d-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="4db7d-122">Při inicializaci pole, na které ukazuje, `characterArray()` obsahuje "x", "y" a "z".</span><span class="sxs-lookup"><span data-stu-id="4db7d-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="4db7d-123">Vzhledem k tomu `characterArray` , že proměnná je `ReadOnly` , nelze po inicializaci změnit její hodnotu; to znamená, že k ní nelze přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="4db7d-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="4db7d-124">Můžete však změnit hodnoty jednoho nebo více členů pole.</span><span class="sxs-lookup"><span data-stu-id="4db7d-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="4db7d-125">Po volání procedury se pole, na které se odkazuje, `ChangeArrayElement` `characterArray()` drží "x", "M" a "z".</span><span class="sxs-lookup"><span data-stu-id="4db7d-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="4db7d-126">Všimněte si, že je to podobné jako deklarace parametru procedury pro [ByVal](byval.md), což brání postupu v změně samotného argumentu volání, ale umožňuje změnit jeho členy.</span><span class="sxs-lookup"><span data-stu-id="4db7d-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="4db7d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="4db7d-127">Example</span></span>

<span data-ttu-id="4db7d-128">Následující příklad definuje `ReadOnly` vlastnost pro datum, kdy byl zaměstnanec přijat.</span><span class="sxs-lookup"><span data-stu-id="4db7d-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="4db7d-129">Třída ukládá hodnotu vlastnosti interně jako `Private` proměnnou a pouze kód uvnitř třídy může tuto hodnotu změnit.</span><span class="sxs-lookup"><span data-stu-id="4db7d-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="4db7d-130">Vlastnost je však `Public` a jakýkoli kód, který má přístup ke třídě, může číst vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4db7d-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="4db7d-131">`ReadOnly`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="4db7d-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="4db7d-132">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="4db7d-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="4db7d-133">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="4db7d-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="4db7d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="4db7d-134">See also</span></span>

- [<span data-ttu-id="4db7d-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="4db7d-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="4db7d-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4db7d-136">Keywords</span></span>](../keywords/index.md)

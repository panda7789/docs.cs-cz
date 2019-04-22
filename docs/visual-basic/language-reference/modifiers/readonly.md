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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825388"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="01f89-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01f89-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="01f89-103">Určuje, že proměnné nebo vlastnosti lze číst, ale není zapsána.</span><span class="sxs-lookup"><span data-stu-id="01f89-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f89-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01f89-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="01f89-105">pravidla</span><span class="sxs-lookup"><span data-stu-id="01f89-105">Rules</span></span>  
  
-   <span data-ttu-id="01f89-106">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="01f89-106">**Declaration Context.**</span></span> <span data-ttu-id="01f89-107">Můžete použít `ReadOnly` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="01f89-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="01f89-108">To znamená, že deklarace kontext `ReadOnly` elementu musí být třída, struktura nebo modulu a nemůže být zdrojový soubor, obor názvů nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="01f89-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="01f89-109">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="01f89-109">**Combined Modifiers.**</span></span> <span data-ttu-id="01f89-110">Nelze zadat `ReadOnly` spolu s `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="01f89-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="01f89-111">**Přiřazení hodnoty.**</span><span class="sxs-lookup"><span data-stu-id="01f89-111">**Assigning a Value.**</span></span> <span data-ttu-id="01f89-112">Použití kódu `ReadOnly` jeho hodnotu nelze nastavit vlastnost.</span><span class="sxs-lookup"><span data-stu-id="01f89-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="01f89-113">Ale kód, který má přístup k podkladové úložiště můžete přiřadit nebo změňte hodnotu v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="01f89-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="01f89-114">Můžete přiřadit hodnoty k `ReadOnly` proměnné pouze v jeho deklaraci nebo v konstruktoru třídy nebo struktury, ve kterém je definována.</span><span class="sxs-lookup"><span data-stu-id="01f89-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="01f89-115">Kdy použít proměnnou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="01f89-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="01f89-116">Existují situace, ve kterých nelze použít [Const příkaz](../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01f89-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="01f89-117">Například `Const` příkaz nemusí přijmout typ dat, kterou chcete přiřadit, nebo nemusí být schopný vypočítat hodnotu v době kompilace konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="01f89-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="01f89-118">Hodnota nemusí vědět i v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="01f89-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="01f89-119">V těchto případech můžete použít `ReadOnly` proměnnou pro uchování konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01f89-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01f89-120">Pokud je datový typ proměnné typu odkazu, například pole nebo instanci třídy, jejích členů lze změnit i v případě, že je proměnná samotného `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="01f89-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="01f89-121">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="01f89-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="01f89-122">Při inicializaci pole odkazované `characterArray()` blokování "x", "y" a "z".</span><span class="sxs-lookup"><span data-stu-id="01f89-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="01f89-123">Protože proměnné `characterArray` je `ReadOnly`, jeho hodnotu nelze změnit po inicializaci; který je, není možné přiřadit nové pole.</span><span class="sxs-lookup"><span data-stu-id="01f89-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="01f89-124">Však můžete změnit hodnoty jedné nebo více členů pole.</span><span class="sxs-lookup"><span data-stu-id="01f89-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="01f89-125">Následující volání do procedury `changeArrayElement`, pole odkazované `characterArray()` blokování "x", "M" a "z".</span><span class="sxs-lookup"><span data-stu-id="01f89-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="01f89-126">Všimněte si, že je podobná deklaraci parametru postupu bude [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), což zabrání změně samotného argumentu volajícího procesu, ale umožňuje měnit její členy.</span><span class="sxs-lookup"><span data-stu-id="01f89-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f89-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="01f89-127">Example</span></span>  
 <span data-ttu-id="01f89-128">Následující příklad definuje `ReadOnly` vlastnost pro datum přijetí zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="01f89-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="01f89-129">Vlastnost hodnota interně jako třídy úložiště `Private` tuto hodnotu můžete změnit proměnné a to pouze kód uvnitř třídy.</span><span class="sxs-lookup"><span data-stu-id="01f89-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="01f89-130">Vlastnost je však `Public`, a vlastnost může přečíst jakýkoli kód, který může přistupovat k třídě.</span><span class="sxs-lookup"><span data-stu-id="01f89-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="01f89-131">`ReadOnly` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="01f89-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="01f89-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="01f89-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="01f89-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="01f89-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="01f89-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01f89-134">See also</span></span>

- [<span data-ttu-id="01f89-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="01f89-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="01f89-136">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="01f89-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

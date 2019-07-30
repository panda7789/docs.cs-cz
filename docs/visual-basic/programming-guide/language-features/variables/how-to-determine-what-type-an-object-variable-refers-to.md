---
title: 'Postupy: Určete, na jaký typ proměnná objektu odkazuje (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626566"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="07f3f-102">Postupy: Určete, na jaký typ proměnná objektu odkazuje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07f3f-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="07f3f-103">Proměnná objektu obsahuje ukazatel na data, která jsou uložená jinde.</span><span class="sxs-lookup"><span data-stu-id="07f3f-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="07f3f-104">Typ těchto dat se může během běhu změnit.</span><span class="sxs-lookup"><span data-stu-id="07f3f-104">The type of that data can change during run time.</span></span> <span data-ttu-id="07f3f-105">V každém okamžiku můžete použít <xref:System.Type.GetTypeCode%2A> metodu k určení aktuálního typu za běhu nebo operátora [typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) k zjištění, zda je aktuální typ běhu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="07f3f-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="07f3f-106">Určení přesného typu, na který aktuálně odkazuje proměnná objektu</span><span class="sxs-lookup"><span data-stu-id="07f3f-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="07f3f-107">Na objektovou proměnnou volejte <xref:System.Object.GetType%2A> metodu pro <xref:System.Type?displayProperty=nameWithType> načtení objektu.</span><span class="sxs-lookup"><span data-stu-id="07f3f-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="07f3f-108">U třídy zavolejte sdílenou metodu <xref:System.Type.GetTypeCode%2A> pro načtení <xref:System.TypeCode> hodnoty výčtu pro typ objektu. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="07f3f-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="07f3f-109">Můžete otestovat hodnotu výčtu <xref:System.TypeCode> na základě toho, co členové výčtu mají zájem, `Double`například.</span><span class="sxs-lookup"><span data-stu-id="07f3f-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="07f3f-110">Určení, zda je typ objektové proměnné kompatibilní se zadaným typem</span><span class="sxs-lookup"><span data-stu-id="07f3f-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="07f3f-111">Použijte operátor v kombinaci s operátorem [is](../../../../visual-basic/language-reference/operators/is-operator.md) k otestování objektu s `TypeOf`... `TypeOf` `Is` výraz.</span><span class="sxs-lookup"><span data-stu-id="07f3f-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="07f3f-112">`TypeOf`... `Is` výraz vrátí`True` , pokud je typ modulu runtime objektu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="07f3f-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="07f3f-113">Kritérium kompatibility závisí na tom, zda je zadaný typ třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="07f3f-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="07f3f-114">Obecně jsou typy kompatibilní, pokud je objekt stejného typu jako, dědí z nebo implementuje zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="07f3f-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="07f3f-115">Další informace naleznete v tématu [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="07f3f-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="07f3f-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="07f3f-116">Compiling the Code</span></span>

<span data-ttu-id="07f3f-117">Všimněte si, že zadaný typ nemůže být proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="07f3f-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="07f3f-118">Musí se jednat o název definovaného typu, jako je například třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="07f3f-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="07f3f-119">To zahrnuje vnitřní typy, jako `Integer` jsou `String`a.</span><span class="sxs-lookup"><span data-stu-id="07f3f-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="07f3f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07f3f-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="07f3f-121">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="07f3f-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="07f3f-122">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="07f3f-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="07f3f-123">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="07f3f-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

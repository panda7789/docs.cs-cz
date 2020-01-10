---
title: 'Postupy: Určení, na jaký typ proměnná objektu odkazuje'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: b3778a170759f685db78e7dcde219138196f9eca
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344190"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="7aed8-102">Postupy: Určení, na jaký typ proměnná objektu odkazuje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aed8-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="7aed8-103">Proměnná objektu obsahuje ukazatel na data, která jsou uložená jinde.</span><span class="sxs-lookup"><span data-stu-id="7aed8-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="7aed8-104">Typ těchto dat se může během běhu změnit.</span><span class="sxs-lookup"><span data-stu-id="7aed8-104">The type of that data can change during run time.</span></span> <span data-ttu-id="7aed8-105">V každém okamžiku můžete použít metodu <xref:System.Type.GetTypeCode%2A> k určení aktuálního typu běhu nebo [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) k zjištění, zda je aktuální typ běhu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="7aed8-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="7aed8-106">Určení přesného typu, na který aktuálně odkazuje proměnná objektu</span><span class="sxs-lookup"><span data-stu-id="7aed8-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="7aed8-107">Na objektovou proměnnou volejte metodu <xref:System.Object.GetType%2A> pro načtení objektu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7aed8-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="7aed8-108">Na <xref:System.Type?displayProperty=nameWithType> třídy zavolejte <xref:System.Type.GetTypeCode%2A> sdílené metody, aby se načetla hodnota výčtu <xref:System.TypeCode> pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="7aed8-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="7aed8-109">Můžete otestovat <xref:System.TypeCode> hodnotu výčtu na základě toho, co členové výčtu mají zájem, jako je například `Double`.</span><span class="sxs-lookup"><span data-stu-id="7aed8-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="7aed8-110">Určení, zda je typ objektové proměnné kompatibilní se zadaným typem</span><span class="sxs-lookup"><span data-stu-id="7aed8-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="7aed8-111">Použijte operátor `TypeOf` v kombinaci s [operátorem is](../../../../visual-basic/language-reference/operators/is-operator.md) k otestování objektu pomocí výrazu `TypeOf`...`Is`.</span><span class="sxs-lookup"><span data-stu-id="7aed8-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="7aed8-112">Výraz `TypeOf`...`Is` vrací `True`, pokud je typ modulu runtime objektu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="7aed8-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="7aed8-113">Kritérium kompatibility závisí na tom, zda je zadaný typ třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7aed8-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="7aed8-114">Obecně jsou typy kompatibilní, pokud je objekt stejného typu jako, dědí z nebo implementuje zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="7aed8-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="7aed8-115">Další informace naleznete v tématu [operátor typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7aed8-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="7aed8-116">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7aed8-116">Compile the code</span></span>

<span data-ttu-id="7aed8-117">Všimněte si, že zadaný typ nemůže být proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="7aed8-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="7aed8-118">Musí se jednat o název definovaného typu, jako je například třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7aed8-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="7aed8-119">To zahrnuje vnitřní typy, jako `Integer` a `String`.</span><span class="sxs-lookup"><span data-stu-id="7aed8-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aed8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7aed8-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="7aed8-121">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7aed8-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="7aed8-122">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7aed8-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="7aed8-123">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="7aed8-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

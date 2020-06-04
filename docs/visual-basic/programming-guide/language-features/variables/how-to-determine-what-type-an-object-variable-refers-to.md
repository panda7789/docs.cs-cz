---
title: 'Postupy: Určení, na jaký typ proměnná objektu odkazuje'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410487"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="f0195-102">Postupy: Určení, na jaký typ proměnná objektu odkazuje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0195-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="f0195-103">Proměnná objektu obsahuje ukazatel na data, která jsou uložená jinde.</span><span class="sxs-lookup"><span data-stu-id="f0195-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="f0195-104">Typ těchto dat se může během běhu změnit.</span><span class="sxs-lookup"><span data-stu-id="f0195-104">The type of that data can change during run time.</span></span> <span data-ttu-id="f0195-105">V každém okamžiku můžete použít <xref:System.Type.GetTypeCode%2A> metodu k určení aktuálního typu za běhu nebo [operátora typeof](../../../language-reference/operators/typeof-operator.md) k zjištění, zda je aktuální typ běhu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="f0195-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="f0195-106">Určení přesného typu, na který aktuálně odkazuje proměnná objektu</span><span class="sxs-lookup"><span data-stu-id="f0195-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="f0195-107">Na objektovou proměnnou volejte <xref:System.Object.GetType%2A> metodu pro načtení <xref:System.Type?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="f0195-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="f0195-108">U <xref:System.Type?displayProperty=nameWithType> třídy zavolejte sdílenou metodu <xref:System.Type.GetTypeCode%2A> pro načtení <xref:System.TypeCode> hodnoty výčtu pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="f0195-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="f0195-109">Můžete otestovat <xref:System.TypeCode> hodnotu výčtu na základě toho, co členové výčtu mají zájem, například `Double` .</span><span class="sxs-lookup"><span data-stu-id="f0195-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="f0195-110">Určení, zda je typ objektové proměnné kompatibilní se zadaným typem</span><span class="sxs-lookup"><span data-stu-id="f0195-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="f0195-111">Použijte `TypeOf` operátor v kombinaci s [operátorem is](../../../language-reference/operators/is-operator.md) k otestování objektu pomocí `TypeOf` výrazu.... `Is`</span><span class="sxs-lookup"><span data-stu-id="f0195-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="f0195-112">`TypeOf`Výraz... `Is` vrátí, `True` Pokud je typ modulu runtime objektu kompatibilní se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="f0195-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="f0195-113">Kritérium kompatibility závisí na tom, zda je zadaný typ třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0195-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="f0195-114">Obecně jsou typy kompatibilní, pokud je objekt stejného typu jako, dědí z nebo implementuje zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="f0195-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="f0195-115">Další informace naleznete v tématu [operátor typeof](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f0195-115">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="f0195-116">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="f0195-116">Compile the code</span></span>

<span data-ttu-id="f0195-117">Všimněte si, že zadaný typ nemůže být proměnná nebo výraz.</span><span class="sxs-lookup"><span data-stu-id="f0195-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="f0195-118">Musí se jednat o název definovaného typu, jako je například třída, struktura nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0195-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="f0195-119">To zahrnuje vnitřní typy, jako jsou `Integer` a `String` .</span><span class="sxs-lookup"><span data-stu-id="f0195-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0195-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0195-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="f0195-121">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="f0195-121">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="f0195-122">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="f0195-122">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="f0195-123">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="f0195-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)

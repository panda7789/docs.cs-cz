---
title: 'Postupy: Přiřazení jednoho pole ke druhému'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413076"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="2a209-102">Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a209-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="2a209-103">Vzhledem k tomu, že pole jsou objekty, můžete je použít v příkazech přiřazení jako jiné typy objektů.</span><span class="sxs-lookup"><span data-stu-id="2a209-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="2a209-104">Proměnná pole obsahuje ukazatel na data tvořící prvky pole a informace o rozměrech a délce a přiřazení kopíruje pouze tento ukazatel.</span><span class="sxs-lookup"><span data-stu-id="2a209-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="2a209-105">Přiřazení jednoho pole k jinému poli</span><span class="sxs-lookup"><span data-stu-id="2a209-105">To assign one array to another array</span></span>

1. <span data-ttu-id="2a209-106">Zajistěte, aby obě pole měly stejný rozměr (počet rozměrů) a kompatibilní datové typy prvků.</span><span class="sxs-lookup"><span data-stu-id="2a209-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="2a209-107">Použijte standardní příkaz přiřazení pro přiřazení zdrojového pole k cílovému poli.</span><span class="sxs-lookup"><span data-stu-id="2a209-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="2a209-108">Neprovádějte žádné názvy polí pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="2a209-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="2a209-109">Když přiřadíte jedno pole k druhému, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="2a209-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="2a209-110">**Stejné pořadí.**</span><span class="sxs-lookup"><span data-stu-id="2a209-110">**Equal Ranks.**</span></span> <span data-ttu-id="2a209-111">Rozměr (počet rozměrů) cílového pole musí být stejný jako zdroj pole.</span><span class="sxs-lookup"><span data-stu-id="2a209-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="2a209-112">Za předpokladu, že je pořadí dvou polí stejné, dimenze nemusí být stejné.</span><span class="sxs-lookup"><span data-stu-id="2a209-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="2a209-113">Počet prvků v dané dimenzi se může během přiřazení změnit.</span><span class="sxs-lookup"><span data-stu-id="2a209-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="2a209-114">**Typy prvků.**</span><span class="sxs-lookup"><span data-stu-id="2a209-114">**Element Types.**</span></span> <span data-ttu-id="2a209-115">Obě pole musí mít elementy *typu odkazu* , nebo obě pole musí mít elementy *typu hodnoty* .</span><span class="sxs-lookup"><span data-stu-id="2a209-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="2a209-116">Další informace naleznete v tématu [typy hodnot a typy odkazů](../data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2a209-116">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="2a209-117">Pokud mají obě pole elementy typu hodnoty, musí být datové typy elementu přesně stejné.</span><span class="sxs-lookup"><span data-stu-id="2a209-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="2a209-118">Jedinou výjimkou je, že můžete přiřadit pole `Enum` prvků k poli základního typu, který `Enum` .</span><span class="sxs-lookup"><span data-stu-id="2a209-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="2a209-119">Pokud mají obě pole elementy typu odkazu, typ zdrojového elementu musí být odvozen od typu cílového elementu.</span><span class="sxs-lookup"><span data-stu-id="2a209-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="2a209-120">V takovém případě mají dvě pole stejný vztah dědičnosti jako jejich prvky.</span><span class="sxs-lookup"><span data-stu-id="2a209-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="2a209-121">Tato metoda se nazývá *kovariance pole*.</span><span class="sxs-lookup"><span data-stu-id="2a209-121">This is called *array covariance*.</span></span>

<span data-ttu-id="2a209-122">Kompilátor ohlásí chybu, pokud jsou uvedená pravidla porušena, například pokud nejsou datové typy kompatibilní nebo pořadí nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="2a209-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="2a209-123">Do kódu můžete přidat zpracování chyb, abyste se ujistili, že jsou pole kompatibilní před pokusem o přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2a209-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="2a209-124">Klíčové slovo [operátoru TryCast](../../../language-reference/operators/trycast-operator.md) můžete použít také v případě, že chcete zabránit vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="2a209-124">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a209-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a209-125">See also</span></span>

- [<span data-ttu-id="2a209-126">Pole</span><span class="sxs-lookup"><span data-stu-id="2a209-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="2a209-127">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="2a209-127">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="2a209-128">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="2a209-128">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="2a209-129">Převody polí</span><span class="sxs-lookup"><span data-stu-id="2a209-129">Array Conversions</span></span>](../data-types/array-conversions.md)

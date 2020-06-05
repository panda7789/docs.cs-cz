---
title: 'Postupy: Uchování více než jedné hodnoty v proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393893"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="2221f-102">Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2221f-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="2221f-103">Proměnná obsahuje více než jednu hodnotu, pokud deklarujete jako *složený datový typ*.</span><span class="sxs-lookup"><span data-stu-id="2221f-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="2221f-104">[Složené datové typy](composite-data-types.md) zahrnují struktury, pole a třídy.</span><span class="sxs-lookup"><span data-stu-id="2221f-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="2221f-105">Proměnná složeného datového typu může obsahovat kombinaci základních datových typů a dalších složených typů.</span><span class="sxs-lookup"><span data-stu-id="2221f-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="2221f-106">Struktury a třídy mohou uchovávat kód i data.</span><span class="sxs-lookup"><span data-stu-id="2221f-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="2221f-107">Uložení více než jedné hodnoty v proměnné</span><span class="sxs-lookup"><span data-stu-id="2221f-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="2221f-108">Určete, jaký typ složeného dat chcete pro proměnnou použít.</span><span class="sxs-lookup"><span data-stu-id="2221f-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="2221f-109">Pokud se složený datový typ ještě nedefinuje, definujte ho, aby ho vaše proměnná mohla použít.</span><span class="sxs-lookup"><span data-stu-id="2221f-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="2221f-110">Definujte strukturu pomocí [příkazu struktury](../../../language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="2221f-111">Definujte pole pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="2221f-112">Definujte třídu pomocí [příkazu třídy](../../../language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="2221f-113">Deklarujte proměnnou pomocí `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2221f-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="2221f-114">Použijte název proměnné s `As` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="2221f-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="2221f-115">Použijte `As` klíčové slovo s názvem vhodného složeného datového typu.</span><span class="sxs-lookup"><span data-stu-id="2221f-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="2221f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2221f-116">See also</span></span>

- [<span data-ttu-id="2221f-117">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2221f-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="2221f-118">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="2221f-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="2221f-119">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="2221f-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="2221f-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="2221f-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="2221f-121">Pole</span><span class="sxs-lookup"><span data-stu-id="2221f-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="2221f-122">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2221f-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="2221f-123">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="2221f-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)

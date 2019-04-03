---
title: 'Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835281"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="96b5d-102">Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96b5d-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="96b5d-103">Protože pole jsou objekty, které lze využít v přiřazovací příkazy jako ostatní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="96b5d-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="96b5d-104">Proměnné pole tvořící prvky pole a informace o počet rozměrů a délka dat obsahuje ukazatel a přiřazení zkopíruje pouze tento ukazatel.</span><span class="sxs-lookup"><span data-stu-id="96b5d-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="96b5d-105">K přiřazení jednoho pole ke druhému</span><span class="sxs-lookup"><span data-stu-id="96b5d-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="96b5d-106">Ujistěte se, že dvě pole mají stejné pořadí (počet rozměrů) a kompatibilní element datové typy.</span><span class="sxs-lookup"><span data-stu-id="96b5d-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="96b5d-107">Použijte standardní přiřazovací příkaz přiřaďte pole zdrojového do cílového pole.</span><span class="sxs-lookup"><span data-stu-id="96b5d-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="96b5d-108">Nepostupujte podle buď název pole v závorkách.</span><span class="sxs-lookup"><span data-stu-id="96b5d-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="96b5d-109">Při přiřazení jednoho pole do jiného, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="96b5d-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="96b5d-110">**Stejné rozměry.**</span><span class="sxs-lookup"><span data-stu-id="96b5d-110">**Equal Ranks.**</span></span> <span data-ttu-id="96b5d-111">Rozměr (počet rozměrů) cílového pole musí být stejné jako u zdrojového pole.</span><span class="sxs-lookup"><span data-stu-id="96b5d-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="96b5d-112">Pokud jsou stejné rozměry dvě pole, není potřeba rovnat dimenze.</span><span class="sxs-lookup"><span data-stu-id="96b5d-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="96b5d-113">Během přiřazování můžete změnit počet prvků v dané dimenzi.</span><span class="sxs-lookup"><span data-stu-id="96b5d-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="96b5d-114">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="96b5d-114">**Element Types.**</span></span> <span data-ttu-id="96b5d-115">Buď obě pole musí mít *odkazovat na typ* elementy nebo obě pole musí mít *typ hodnoty* elementy.</span><span class="sxs-lookup"><span data-stu-id="96b5d-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="96b5d-116">Další informace najdete v tématu [typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="96b5d-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="96b5d-117">Pokud obě pole mají prvky typu hodnoty, element datové typy, které musí být přesně stejný.</span><span class="sxs-lookup"><span data-stu-id="96b5d-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="96b5d-118">Jedinou výjimkou je, že můžete přiřadit pole `Enum` prvky do pole Základní typ, který `Enum`.</span><span class="sxs-lookup"><span data-stu-id="96b5d-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="96b5d-119">Pokud obě pole mít odkaz na typ prvků, typ zdrojového prvku musí být odvozen z typu cílového elementu.</span><span class="sxs-lookup"><span data-stu-id="96b5d-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="96b5d-120">Pokud tomu tak, máte dvě pole stejné relaci dědičnosti jako jejich prvky.</span><span class="sxs-lookup"><span data-stu-id="96b5d-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="96b5d-121">Tento postup se nazývá *kovariance polí*.</span><span class="sxs-lookup"><span data-stu-id="96b5d-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="96b5d-122">Kompilátor hlásí chybu, pokud se výše uvedených pravidel se poruší, například pokud datové typy, které nejsou kompatibilní, nebo je pořadí nerovnost.</span><span class="sxs-lookup"><span data-stu-id="96b5d-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="96b5d-123">Můžete přidat do vašeho kódu, abyste měli jistotu, že tato pole jsou kompatibilní před pokusem o přiřazení pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="96b5d-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="96b5d-124">Můžete také použít [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo, pokud chcete, aby se zabránilo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="96b5d-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b5d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96b5d-125">See also</span></span>

- [<span data-ttu-id="96b5d-126">Pole</span><span class="sxs-lookup"><span data-stu-id="96b5d-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="96b5d-127">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="96b5d-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="96b5d-128">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="96b5d-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="96b5d-129">Převody polí</span><span class="sxs-lookup"><span data-stu-id="96b5d-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)

---
title: "Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0dd2d678bbfdeaa6b12b5b5a4f69d0fbca8c1944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="3bdcb-102">Postupy: Přiřazení jednoho pole ke druhému (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bdcb-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="3bdcb-103">Vzhledem k tomu, že pole jsou objekty, můžete je používat v příkazech přiřazení jako ostatní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="3bdcb-104">Proměnné pole obsahuje ukazatele na data tvořících elementy pole a informace o pořadí a délku a přiřazení zkopíruje pouze tento ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="3bdcb-105">K přiřazení jednoho pole ke druhému</span><span class="sxs-lookup"><span data-stu-id="3bdcb-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="3bdcb-106">Zajistěte, aby tato dvě pole element kompatibilní datové typy a stejné pořadí (počet dimenzí).</span><span class="sxs-lookup"><span data-stu-id="3bdcb-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="3bdcb-107">Příkaz standardní přiřazení použijte přiřadit zdrojové pole cílového pole.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="3bdcb-108">Nepostupujte podle buď název pole v závorkách.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="3bdcb-109">Při přiřazení jednoho pole do druhého, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="3bdcb-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="3bdcb-110">**Stejné pořadí.**</span><span class="sxs-lookup"><span data-stu-id="3bdcb-110">**Equal Ranks.**</span></span> <span data-ttu-id="3bdcb-111">Pořadí (počet dimenzí) cílového pole musí být stejná jako u zdrojové pole.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="3bdcb-112">Zadané pořadí polí dvě shodné, není potřeba být stejná dimenze.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="3bdcb-113">Počet elementů v dané dimenzi lze změnit během přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="3bdcb-114">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="3bdcb-114">**Element Types.**</span></span> <span data-ttu-id="3bdcb-115">Musí mít buď obě pole *odkazují na typ* elementy nebo obě pole musí mít *typ hodnoty* elementy.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="3bdcb-116">Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="3bdcb-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="3bdcb-117">Pokud obě pole elementy typu hodnotu, datové typy element musí být přesně stejný.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="3bdcb-118">Jedinou výjimkou je, že můžete přiřadit pole `Enum` elementy na pole Základní typ, který `Enum`.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="3bdcb-119">Pokud obě pole mít odkaz na typ elementů, element typ zdroje musí být odvozený od typu cílového elementu.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="3bdcb-120">Pokud to tento případ, dvě pole mají stejný vztah dědičnosti jako jejich elementů.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="3bdcb-121">To se označuje jako *kovariance polí*.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="3bdcb-122">Kompilátor hlásí chybu, pokud výše uvedených pravidel je porušena, například pokud typy dat není kompatibilní nebo je pořadí nerovnají.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="3bdcb-123">Můžete přidat do kódu a ujistěte se, že tato pole jsou kompatibilní před pokusem o přiřazení zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="3bdcb-124">Můžete také [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md) – klíčové slovo, pokud chcete, aby se zabránilo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="3bdcb-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdcb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bdcb-125">See Also</span></span>  
 [<span data-ttu-id="3bdcb-126">Pole</span><span class="sxs-lookup"><span data-stu-id="3bdcb-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="3bdcb-127">Řešení potíží s poli</span><span class="sxs-lookup"><span data-stu-id="3bdcb-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="3bdcb-128">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="3bdcb-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="3bdcb-129">Převody pole</span><span class="sxs-lookup"><span data-stu-id="3bdcb-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)

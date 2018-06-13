---
title: Řešení potíží s poli (Visual basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 4ab6d376ad8652e460e33c4f2c3285e8c80286fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654258"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="91d87-102">Řešení potíží s poli (Visual basic)</span><span class="sxs-lookup"><span data-stu-id="91d87-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="91d87-103">Tato stránka obsahuje některé běžné problémy, ke kterým dochází při práci s poli.</span><span class="sxs-lookup"><span data-stu-id="91d87-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="91d87-104">Chyby při kompilaci deklarace a inicializace pole</span><span class="sxs-lookup"><span data-stu-id="91d87-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="91d87-105">Chyby při kompilaci mohou vyplývat z neporozumění pravidla pro deklarování, vytváření a inicializace polí.</span><span class="sxs-lookup"><span data-stu-id="91d87-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="91d87-106">Nejčastější příčinou chyb jsou následující:</span><span class="sxs-lookup"><span data-stu-id="91d87-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="91d87-107">Poskytnutí [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzule po zadání dimenze délky v deklarace proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="91d87-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="91d87-108">Následující řádky kódu ukazují neplatná deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="91d87-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="91d87-109">Určení délky dimenze pro více než pole nejvyšší úrovně Vícenásobná pole.</span><span class="sxs-lookup"><span data-stu-id="91d87-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="91d87-110">Následující řádek kódu ukazuje neplatný deklaraci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="91d87-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="91d87-111">Vynechání `New` – klíčové slovo při zadávání hodnot prvků.</span><span class="sxs-lookup"><span data-stu-id="91d87-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="91d87-112">Následující řádek kódu ukazuje neplatný deklaraci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="91d87-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="91d87-113">Poskytnutí `New` klauzule bez složené závorky (`{}`).</span><span class="sxs-lookup"><span data-stu-id="91d87-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="91d87-114">Následující řádky kódu ukazují neplatná deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="91d87-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="91d87-115">Přístup k pole mimo rozsah</span><span class="sxs-lookup"><span data-stu-id="91d87-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="91d87-116">Proces inicializace pole přiřadí horní mez a dolní hranice Každá dimenze.</span><span class="sxs-lookup"><span data-stu-id="91d87-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="91d87-117">Každý přístup k elementu pole musíte zadat platný index nebo dolní index pro každé dimenze.</span><span class="sxs-lookup"><span data-stu-id="91d87-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="91d87-118">Pokud žádný index je menší než její dolní mez nebo vyšší než horní mez, <xref:System.IndexOutOfRangeException> dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="91d87-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="91d87-119">Kompilátor nerozpozná takové chyby, takže dojde k chybě za běhu.</span><span class="sxs-lookup"><span data-stu-id="91d87-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="91d87-120">Určení hranice</span><span class="sxs-lookup"><span data-stu-id="91d87-120">Determining Bounds</span></span>  
 <span data-ttu-id="91d87-121">Pokud jiný součást předá pole do kódu, například jako argumentu procedury neznáte velikost tohoto pole nebo délky jeho dimenzí.</span><span class="sxs-lookup"><span data-stu-id="91d87-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="91d87-122">Vždy byste měli zjistit horní mez pro každé dimenze pole před dalším pokusem o přístup k žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="91d87-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="91d87-123">Pokud byla vytvořena pole některé prostředky než jazyka Visual Basic `New` klauzuli dolní mez může být něco jiného než 0 a je nejbezpečnější určit, že dolní mez.</span><span class="sxs-lookup"><span data-stu-id="91d87-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="91d87-124">Určení dimenze</span><span class="sxs-lookup"><span data-stu-id="91d87-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="91d87-125">Při určování hranice multidimenzionálního pole, vezměte v potaz, jak určit dimenzi.</span><span class="sxs-lookup"><span data-stu-id="91d87-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="91d87-126">`dimension` Parametry <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založené na 0 při `Rank` parametry Visual Basicu <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A> funkce jsou založené na 1.</span><span class="sxs-lookup"><span data-stu-id="91d87-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d87-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="91d87-127">See Also</span></span>  
 [<span data-ttu-id="91d87-128">Pole</span><span class="sxs-lookup"><span data-stu-id="91d87-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="91d87-129">Postupy: Inicializace proměnné pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91d87-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)

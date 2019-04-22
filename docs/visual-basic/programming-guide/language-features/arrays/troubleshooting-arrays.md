---
title: Řešení potíží s poli (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833370"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="d8b51-102">Řešení potíží s poli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8b51-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="d8b51-103">Tato stránka obsahuje některé běžné problémy, které se mohou vyskytnout při práci s poli.</span><span class="sxs-lookup"><span data-stu-id="d8b51-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="d8b51-104">Chyby při kompilaci deklarace a inicializace pole</span><span class="sxs-lookup"><span data-stu-id="d8b51-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="d8b51-105">Chyby při kompilaci mohou vyplývat z neporozumění pravidla pro deklarování, vytváření a inicializaci polí.</span><span class="sxs-lookup"><span data-stu-id="d8b51-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="d8b51-106">Nejběžnější příčiny chyby jsou následující:</span><span class="sxs-lookup"><span data-stu-id="d8b51-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="d8b51-107">Zadávání [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzule po zadání délky dimenzí v deklaraci proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="d8b51-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="d8b51-108">Následující řádky kódu zobrazit neplatná deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d8b51-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="d8b51-109">Určení délky dimenzí pro více než pole nejvyšší úrovně vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="d8b51-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="d8b51-110">Následující řádek kódu obsahuje neplatnou deklarací tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d8b51-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="d8b51-111">Vynechání `New` – klíčové slovo při zadávání hodnot prvků.</span><span class="sxs-lookup"><span data-stu-id="d8b51-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="d8b51-112">Následující řádek kódu obsahuje neplatnou deklarací tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d8b51-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="d8b51-113">Zadávání `New` klauzule bez složených závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="d8b51-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="d8b51-114">Následující řádky kódu zobrazit neplatná deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d8b51-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="d8b51-115">Přístup k poli mimo rozsah</span><span class="sxs-lookup"><span data-stu-id="d8b51-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="d8b51-116">Proces inicializace pole přiřadí horní a dolní mez každé dimenze.</span><span class="sxs-lookup"><span data-stu-id="d8b51-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="d8b51-117">Každý přístup k elementu pole musíte zadat platný index nebo dolní index pro každou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="d8b51-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="d8b51-118">Pokud je jakýkoli index pod její dolní mez nebo nad horní mez <xref:System.IndexOutOfRangeException> dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d8b51-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="d8b51-119">Kompilátor nemůže rozpoznat takové chyby, takže dojde k chybě za běhu.</span><span class="sxs-lookup"><span data-stu-id="d8b51-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="d8b51-120">Určení hranic</span><span class="sxs-lookup"><span data-stu-id="d8b51-120">Determining Bounds</span></span>  
 <span data-ttu-id="d8b51-121">Pokud jiná komponenta předává pole do kódu, například jako argumentu procedury si nejste jisti velikost pole nebo délky jeho rozměrů.</span><span class="sxs-lookup"><span data-stu-id="d8b51-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="d8b51-122">Vždy byste měli určit horní mez pro každou dimenzi pole před pokusem o přístup k žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="d8b51-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="d8b51-123">Pokud byl vytvořen pole některé prostředky než v jazyce Visual Basic `New` klauzule dolní mez může být něco jiného než 0 a je nejbezpečnější určit, že dolní mez.</span><span class="sxs-lookup"><span data-stu-id="d8b51-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="d8b51-124">Určení dimenze</span><span class="sxs-lookup"><span data-stu-id="d8b51-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="d8b51-125">Při určování hranice vícerozměrného pole, zajistíme, jak specifikujete dimenze.</span><span class="sxs-lookup"><span data-stu-id="d8b51-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="d8b51-126">`dimension` Parametry <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založeny na 0 při `Rank` parametrů jazyka Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A> funkce jsou založené na 1.</span><span class="sxs-lookup"><span data-stu-id="d8b51-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b51-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8b51-127">See also</span></span>

- [<span data-ttu-id="d8b51-128">Pole</span><span class="sxs-lookup"><span data-stu-id="d8b51-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d8b51-129">Postupy: Inicializace proměnné pole v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8b51-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)

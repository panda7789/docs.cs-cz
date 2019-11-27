---
title: Řešení potíží s poli
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349069"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="3748c-102">Řešení potíží s poli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3748c-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="3748c-103">Tato stránka obsahuje některé běžné problémy, které mohou nastat při práci s poli.</span><span class="sxs-lookup"><span data-stu-id="3748c-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="3748c-104">Chyby kompilace, které deklaruje a inicializuje pole</span><span class="sxs-lookup"><span data-stu-id="3748c-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="3748c-105">Chyby kompilace mohou nastat při nepochopení pravidel pro deklarování, vytváření a inicializaci polí.</span><span class="sxs-lookup"><span data-stu-id="3748c-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="3748c-106">Nejběžnější příčiny chyb jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3748c-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="3748c-107">Zadání nové klauzule [operátoru](../../../../visual-basic/language-reference/operators/new-operator.md) po určení délek dimenzí v deklaraci proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="3748c-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="3748c-108">Následující řádky kódu ukazují neplatné deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3748c-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="3748c-109">Určení délek dimenzí pro více než pole nejvyšší úrovně vícenásobného pole.</span><span class="sxs-lookup"><span data-stu-id="3748c-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="3748c-110">Následující řádek kódu ukazuje neplatnou deklaraci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3748c-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="3748c-111">Vynechává se klíčové slovo `New` při zadávání hodnot elementu.</span><span class="sxs-lookup"><span data-stu-id="3748c-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="3748c-112">Následující řádek kódu ukazuje neplatnou deklaraci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3748c-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="3748c-113">Poskytnutí klauzule `New` bez složených závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="3748c-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="3748c-114">Následující řádky kódu ukazují neplatné deklarace tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="3748c-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="3748c-115">Přístup k poli je mimo hranice.</span><span class="sxs-lookup"><span data-stu-id="3748c-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="3748c-116">Proces inicializace pole přiřadí horní mez a spodní mez na každou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="3748c-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="3748c-117">Každý přístup k prvku pole musí pro každou dimenzi určovat platný index nebo dolní index.</span><span class="sxs-lookup"><span data-stu-id="3748c-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="3748c-118">Pokud je některý index pod jeho dolní mezí nebo nad jeho horní mez, <xref:System.IndexOutOfRangeException> výsledek výjimky.</span><span class="sxs-lookup"><span data-stu-id="3748c-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="3748c-119">Kompilátor nemůže rozpoznat takovou chybu, takže dojde k chybě v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3748c-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="3748c-120">Určení hranic</span><span class="sxs-lookup"><span data-stu-id="3748c-120">Determining Bounds</span></span>  
 <span data-ttu-id="3748c-121">Pokud jiná komponenta předá pole do kódu, například jako argument procedury, neznáte velikost tohoto pole nebo délky jeho rozměrů.</span><span class="sxs-lookup"><span data-stu-id="3748c-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="3748c-122">Před pokusem o přístup k libovolným prvkům byste měli vždy určit horní mez pro každý rozměr pole.</span><span class="sxs-lookup"><span data-stu-id="3748c-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="3748c-123">Pokud bylo pole Vytvořeno jiným způsobem než Visual Basic `New` klauzule, dolní hranice může být jiná než 0 a je nejbezpečnější, aby bylo možné zjistit, zda je i dolní mez.</span><span class="sxs-lookup"><span data-stu-id="3748c-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="3748c-124">Určení dimenze</span><span class="sxs-lookup"><span data-stu-id="3748c-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="3748c-125">Při určování hranic multidimenzionálního pole se ujistěte, jak zadáte dimenzi.</span><span class="sxs-lookup"><span data-stu-id="3748c-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="3748c-126">Parametry `dimension` <xref:System.Array.GetLowerBound%2A> a <xref:System.Array.GetUpperBound%2A> metody jsou založené na 0, zatímco parametry `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> a <xref:Microsoft.VisualBasic.Information.UBound%2A>ch funkcí jsou založené na 1.</span><span class="sxs-lookup"><span data-stu-id="3748c-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3748c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3748c-127">See also</span></span>

- [<span data-ttu-id="3748c-128">Pole</span><span class="sxs-lookup"><span data-stu-id="3748c-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3748c-129">Postupy: Inicializace proměnné pole v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3748c-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)

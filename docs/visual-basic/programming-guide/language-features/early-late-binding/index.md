---
title: Statické a pozdní vazby (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'early binding [Visual Basic]'
  - 'objects [Visual Basic], late-bound'
  - 'objects [Visual Basic], early-bound'
  - 'objects [Visual Basic], late bound'
  - 'early binding [Visual Basic], Visual Basic compiler'
  - 'binding [Visual Basic], late and early'
  - 'objects [Visual Basic], early bound'
  - 'Visual Basic compiler, early and late binding'
  - 'late binding [Visual Basic]'
  - 'late binding [Visual Basic], Visual Basic compiler'
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="c77d0-102">Statické a pozdní vazby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c77d0-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="c77d0-103">Kompilátor jazyka Visual Basic provádí proces s názvem `binding` když objekt přiřazen do proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="c77d0-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="c77d0-104">Objekt je *časné* při je přiřazena k proměnné deklarované jako konkrétní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="c77d0-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="c77d0-105">Časná vázaným objektům povolení kompilátoru přidělení paměti a provádět další optimalizace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="c77d0-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="c77d0-106">Například následující fragment kódu deklaruje proměnnou typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="c77d0-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="c77d0-107">Protože <xref:System.IO.FileStream> je konkrétní typy objektů, přiřazenou instanci `FS` časná vazba.</span><span class="sxs-lookup"><span data-stu-id="c77d0-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="c77d0-108">Naopak je objekt *pozdní vazby* při je přiřazena k proměnné deklarované jako typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="c77d0-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="c77d0-109">Objekty tohoto typu můžou obsahovat odkazy na libovolný objekt, ale nemají mnohé z výhod časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="c77d0-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="c77d0-110">Například následující fragment kódu deklaruje proměnnou objektu pro objekt vrácený `CreateObject` funkce:</span><span class="sxs-lookup"><span data-stu-id="c77d0-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="c77d0-111">Výhody časná vazba</span><span class="sxs-lookup"><span data-stu-id="c77d0-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="c77d0-112">Časné vazby objektů pokaždé, když je to možné, byste měli použít, protože umožňují kompilátor, aby byl důležité optimalizace, které vrací efektivnější aplikace.</span><span class="sxs-lookup"><span data-stu-id="c77d0-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="c77d0-113">Časné vazby objektů jsou výrazně rychlejší než objekty s pozdní vazbou a byl kód čitelnější a udržovat tím, že s informacemi o tom právě jaký druh objekty používají.</span><span class="sxs-lookup"><span data-stu-id="c77d0-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="c77d0-114">Časná vazba Další výhodou je, že umožňuje užitečných funkcí, jako je doplňování kódu pro automatickou a dynamická Nápověda, protože integrovaného vývojového prostředí (IDE) sady Visual Studio můžete určit přesně jaký typ objektu pracujete s při úpravě kód.</span><span class="sxs-lookup"><span data-stu-id="c77d0-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="c77d0-115">Časné vazby snižuje množství a závažnosti chyby za běhu, protože umožňuje kompilátoru zprávy o chybách při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="c77d0-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c77d0-116">Pozdní vazby jde použít jenom pro přístup ke členům typu, které jsou deklarovány jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="c77d0-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="c77d0-117">Přístup k členům deklarován jako `Friend` nebo `Protected Friend` vede k chybě za běhu.</span><span class="sxs-lookup"><span data-stu-id="c77d0-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77d0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c77d0-118">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="c77d0-119">Doba života objektu: Způsob vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="c77d0-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="c77d0-120">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="c77d0-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

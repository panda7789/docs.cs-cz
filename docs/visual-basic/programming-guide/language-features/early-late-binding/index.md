---
title: Statické a pozdní vazby
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345188"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="6d76d-102">Statické a pozdní vazby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d76d-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="6d76d-103">Kompilátor Visual Basic provádí proces nazvaný `binding`, pokud je objekt přiřazen proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="6d76d-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="6d76d-104">Objekt je *časné vazby* , je-li přiřazen k proměnné deklarované jako pro určitý typ objektu.</span><span class="sxs-lookup"><span data-stu-id="6d76d-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="6d76d-105">Předčasný vázané objekty umožňují kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d76d-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="6d76d-106">Například následující fragment kódu deklaruje proměnnou, která má být typu <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="6d76d-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="6d76d-107">Vzhledem k tomu, že <xref:System.IO.FileStream> je konkrétní typ objektu, je instance přiřazená k `FS` na začátku vazby.</span><span class="sxs-lookup"><span data-stu-id="6d76d-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="6d76d-108">Naopak objekt je *pozdní vazba* , pokud je přiřazena proměnné deklarované jako typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="6d76d-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="6d76d-109">Objekty tohoto typu můžou uchovávat odkazy na libovolný objekt, ale nemají spoustu výhod objektů s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="6d76d-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="6d76d-110">Například následující fragment kódu deklaruje proměnnou objektu pro uchování objektu vráceného funkcí `CreateObject`:</span><span class="sxs-lookup"><span data-stu-id="6d76d-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="6d76d-111">Výhody prvotní vazby</span><span class="sxs-lookup"><span data-stu-id="6d76d-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="6d76d-112">Pokud je to možné, měli byste použít objekty s časnou vazbou, protože umožňují kompilátoru provádět důležité optimalizace, které přinesou efektivnější aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d76d-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="6d76d-113">Objekty s časnou vazbou jsou výrazně rychlejší než objekty s pozdní vazbou a usnadňují čtení a údržbu kódu tím, že přesně udávají, jaký typ objektů se používá.</span><span class="sxs-lookup"><span data-stu-id="6d76d-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="6d76d-114">Další výhodou pro předčasné vázání je to, že umožňuje použití užitečných funkcí, jako je automatické dokončování kódu a dynamické pomoci, protože integrované vývojové prostředí (IDE) sady Visual Studio dokáže přesně určit, se kterým typem objektu pracujete při úpravách znakovou.</span><span class="sxs-lookup"><span data-stu-id="6d76d-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="6d76d-115">Počáteční vazba snižuje počet a závažnost chyb za běhu, protože umožňuje kompilátoru hlásit chyby při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="6d76d-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d76d-116">Pozdní vazbu lze použít pouze pro přístup ke členům typu, které jsou deklarovány jako `Public`.</span><span class="sxs-lookup"><span data-stu-id="6d76d-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="6d76d-117">Při přístupu ke členům deklarovaným jako `Friend` nebo `Protected Friend` dojde k chybě v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6d76d-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d76d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d76d-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="6d76d-119">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="6d76d-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="6d76d-120">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="6d76d-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

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
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410629"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="414a5-102">Statické a pozdní vazby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="414a5-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="414a5-103">Kompilátor Visual Basic provádí proces, který se volá, `binding` když se objekt přiřadí proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="414a5-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="414a5-104">Objekt je *časné vazby* , je-li přiřazen k proměnné deklarované jako pro určitý typ objektu.</span><span class="sxs-lookup"><span data-stu-id="414a5-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="414a5-105">Předčasný vázané objekty umožňují kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="414a5-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="414a5-106">Například následující fragment kódu deklaruje proměnnou, která bude typu <xref:System.IO.FileStream> :</span><span class="sxs-lookup"><span data-stu-id="414a5-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="414a5-107">Vzhledem k tomu <xref:System.IO.FileStream> , že se jedná o konkrétní typ objektu, je instance přiřazená k `FS` předčasnému vázání.</span><span class="sxs-lookup"><span data-stu-id="414a5-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="414a5-108">Naopak objekt je *pozdní vazba* , pokud je přiřazena proměnné deklarované jako typ `Object` .</span><span class="sxs-lookup"><span data-stu-id="414a5-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="414a5-109">Objekty tohoto typu můžou uchovávat odkazy na libovolný objekt, ale nemají spoustu výhod objektů s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="414a5-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="414a5-110">Například následující fragment kódu deklaruje proměnnou objektu pro uchování objektu vráceného `CreateObject` funkcí:</span><span class="sxs-lookup"><span data-stu-id="414a5-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="414a5-111">Výhody prvotní vazby</span><span class="sxs-lookup"><span data-stu-id="414a5-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="414a5-112">Pokud je to možné, měli byste použít objekty s časnou vazbou, protože umožňují kompilátoru provádět důležité optimalizace, které přinesou efektivnější aplikace.</span><span class="sxs-lookup"><span data-stu-id="414a5-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="414a5-113">Objekty s časnou vazbou jsou výrazně rychlejší než objekty s pozdní vazbou a usnadňují čtení a údržbu kódu tím, že přesně udávají, jaký typ objektů se používá.</span><span class="sxs-lookup"><span data-stu-id="414a5-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="414a5-114">Další výhodou pro předčasné vázání je to, že umožňuje použití užitečných funkcí, jako je automatické dokončování kódu a dynamické pomoci, protože integrované vývojové prostředí (IDE) sady Visual Studio dokáže přesně určit, se kterým typem objektu pracujete při úpravách kódu.</span><span class="sxs-lookup"><span data-stu-id="414a5-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="414a5-115">Počáteční vazba snižuje počet a závažnost chyb za běhu, protože umožňuje kompilátoru hlásit chyby při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="414a5-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="414a5-116">Pozdní vazbu lze použít pouze pro přístup ke členům typu, které jsou deklarovány jako `Public` .</span><span class="sxs-lookup"><span data-stu-id="414a5-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="414a5-117">Přístup ke členům deklarovaným jako `Friend` nebo `Protected Friend` má za následek chybu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="414a5-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414a5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="414a5-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="414a5-119">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="414a5-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="414a5-120">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="414a5-120">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)

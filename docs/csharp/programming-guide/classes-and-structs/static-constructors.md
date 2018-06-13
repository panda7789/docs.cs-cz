---
title: Statické konstruktory (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 52c52f68bc3612807b810047044aedbd2c457cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315708"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="bab3a-102">Statické konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bab3a-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="bab3a-103">Statický konstruktor se používá k chybě při inicializaci žádné [statické](../../../csharp/language-reference/keywords/static.md) data, nebo provádět určité akce, které je nutné provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="bab3a-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="bab3a-104">Je volána automaticky dřív, než se vytvoří první instance nebo všechny statické členy odkazují.</span><span class="sxs-lookup"><span data-stu-id="bab3a-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="bab3a-105">Statické konstruktory mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bab3a-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="bab3a-106">Statický konstruktor nemá trvat modifikátory přístupu nebo mít parametry.</span><span class="sxs-lookup"><span data-stu-id="bab3a-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="bab3a-107">Statický konstruktor je automaticky volat za účelem inicializace [třída](../../../csharp/language-reference/keywords/class.md) dřív, než se vytvoří první instance nebo všechny statické členy odkazují.</span><span class="sxs-lookup"><span data-stu-id="bab3a-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="bab3a-108">Statický konstruktor nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="bab3a-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="bab3a-109">Uživatel nemá žádnou kontrolu na provedení statického konstruktoru v programu.</span><span class="sxs-lookup"><span data-stu-id="bab3a-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="bab3a-110">Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="bab3a-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="bab3a-111">Statické konstruktory jsou užitečné také při vytváření Obálka – třídy pro nespravovaného kódu, když konstruktor může volat `LoadLibrary` metoda.</span><span class="sxs-lookup"><span data-stu-id="bab3a-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="bab3a-112">Pokud statického konstruktoru vyvolá výjimku, modul runtime nebude vyvolání ještě jednou a typ zůstanou Neinicializovaný po dobu jeho existence doménu aplikace, ve kterém běží váš program.</span><span class="sxs-lookup"><span data-stu-id="bab3a-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bab3a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bab3a-113">Example</span></span>  
 <span data-ttu-id="bab3a-114">V tomto příkladu třída `Bus` má statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="bab3a-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="bab3a-115">Při první instance `Bus` se vytvoří (`bus1`), statického konstruktoru je vyvolána k inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="bab3a-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="bab3a-116">Ukázkový výstup ověřuje, že statického konstruktoru spouští pouze jednou, i když dvě instance `Bus` vytváří, a aby byl spouštěn před spuštěním konstruktoru instance.</span><span class="sxs-lookup"><span data-stu-id="bab3a-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bab3a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bab3a-117">See Also</span></span>  
 [<span data-ttu-id="bab3a-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bab3a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bab3a-119">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="bab3a-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="bab3a-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="bab3a-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="bab3a-121">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="bab3a-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="bab3a-122">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="bab3a-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

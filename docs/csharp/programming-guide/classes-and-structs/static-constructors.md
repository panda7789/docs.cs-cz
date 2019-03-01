---
title: Statické konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 42fa96ade5eee63d8d1eddff481ac230c92936e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972882"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="50fe7-102">Statické konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="50fe7-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="50fe7-103">Statický konstruktor slouží k inicializaci žádný [statické](../../../csharp/language-reference/keywords/static.md) data, nebo k provedení konkrétní akce, kterou je potřeba provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="50fe7-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="50fe7-104">Je volána automaticky před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.</span><span class="sxs-lookup"><span data-stu-id="50fe7-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="50fe7-105">Statické konstruktory mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="50fe7-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="50fe7-106">Statický konstruktor není trvat modifikátory přístupu nebo mít parametry.</span><span class="sxs-lookup"><span data-stu-id="50fe7-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="50fe7-107">Statický konstruktor je automaticky volána k inicializaci [třídy](../../../csharp/language-reference/keywords/class.md) před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.</span><span class="sxs-lookup"><span data-stu-id="50fe7-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="50fe7-108">Statický konstruktor nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="50fe7-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="50fe7-109">Uživatel nemá žádnou kontrolu na při spouštění statický konstruktor se v programu.</span><span class="sxs-lookup"><span data-stu-id="50fe7-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="50fe7-110">Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="50fe7-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="50fe7-111">Statické konstruktory jsou také užitečné při vytváření obálkových tříd pro nespravovaný kód, konstruktor může volat `LoadLibrary` metody.</span><span class="sxs-lookup"><span data-stu-id="50fe7-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="50fe7-112">Pokud statický konstruktor vyvolá výjimku, modul runtime nebude volat podruhé a typ zůstanou neinicializované po dobu životnosti domény aplikace, ve kterém je spuštěna aplikace.</span><span class="sxs-lookup"><span data-stu-id="50fe7-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fe7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="50fe7-113">Example</span></span>  
 <span data-ttu-id="50fe7-114">V tomto příkladu třída `Bus` má statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="50fe7-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="50fe7-115">Při první instance `Bus` je vytvořen (`bus1`), je vyvolána statický konstruktor k inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="50fe7-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="50fe7-116">Ukázkový výstup ověřuje, že statický konstruktor spouští jenom jednou, i když dvě instance `Bus` jsou vytvořeny, a že běží před spuštěním konstruktoru instance.</span><span class="sxs-lookup"><span data-stu-id="50fe7-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="50fe7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50fe7-117">See also</span></span>

- [<span data-ttu-id="50fe7-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="50fe7-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="50fe7-119">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="50fe7-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="50fe7-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="50fe7-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="50fe7-121">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="50fe7-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="50fe7-122">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="50fe7-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

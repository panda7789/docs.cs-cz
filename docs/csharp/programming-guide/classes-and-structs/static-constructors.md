---
title: Statické konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881918"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="f9f58-102">Statické konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f9f58-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="f9f58-103">Statický konstruktor slouží k inicializaci žádný [statické](../../../csharp/language-reference/keywords/static.md) data, nebo k provedení konkrétní akce, kterou je potřeba provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f9f58-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="f9f58-104">Je volána automaticky před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.</span><span class="sxs-lookup"><span data-stu-id="f9f58-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="f9f58-105">Statické konstruktory mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f9f58-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="f9f58-106">Statický konstruktor není trvat modifikátory přístupu nebo mít parametry.</span><span class="sxs-lookup"><span data-stu-id="f9f58-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="f9f58-107">Statický konstruktor je automaticky volána k inicializaci [třídy](../../../csharp/language-reference/keywords/class.md) před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.</span><span class="sxs-lookup"><span data-stu-id="f9f58-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="f9f58-108">Všimněte si, že když uživatel vyvolá statickou metodu přiřazená události nebo delegáta, a ne v případě, že je přiřazen název statického konstruktoru typu.</span><span class="sxs-lookup"><span data-stu-id="f9f58-108">Note that a type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span>
  
- <span data-ttu-id="f9f58-109">Statický konstruktor nelze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="f9f58-109">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="f9f58-110">Uživatel nemá žádnou kontrolu na při spouštění statický konstruktor se v programu.</span><span class="sxs-lookup"><span data-stu-id="f9f58-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="f9f58-111">Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="f9f58-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="f9f58-112">Statické konstruktory jsou také užitečné při vytváření obálkových tříd pro nespravovaný kód, konstruktor může volat `LoadLibrary` metody.</span><span class="sxs-lookup"><span data-stu-id="f9f58-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="f9f58-113">Pokud statický konstruktor vyvolá výjimku, modul runtime nebude volat podruhé a typ zůstanou neinicializované po dobu životnosti domény aplikace, ve kterém je spuštěna aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9f58-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f58-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f58-114">Example</span></span>  
 <span data-ttu-id="f9f58-115">V tomto příkladu třída `Bus` má statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f9f58-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="f9f58-116">Při první instance `Bus` je vytvořen (`bus1`), je vyvolána statický konstruktor k inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="f9f58-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="f9f58-117">Ukázkový výstup ověřuje, že statický konstruktor spouští jenom jednou, i když dvě instance `Bus` jsou vytvořeny, a že běží před spuštěním konstruktoru instance.</span><span class="sxs-lookup"><span data-stu-id="f9f58-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="f9f58-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9f58-118">See also</span></span>

- [<span data-ttu-id="f9f58-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f9f58-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9f58-120">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="f9f58-120">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f9f58-121">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="f9f58-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="f9f58-122">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="f9f58-122">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="f9f58-123">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="f9f58-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

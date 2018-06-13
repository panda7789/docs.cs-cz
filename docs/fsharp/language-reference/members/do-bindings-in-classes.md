---
title: Vazby do ve třídách (F#)
description: 'Naučte se používat F # "do" vazby v definici třídy, který provádí akce, když je objekt vytvořený, nebo při prvním použití typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565188"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="355af-103">Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="355af-103">do Bindings in Classes</span></span>

<span data-ttu-id="355af-104">A `do` vazby v definici třídy provede akce, když je objekt vytvořený nebo pro statického `do` vazby, pokud typ prvním použití.</span><span class="sxs-lookup"><span data-stu-id="355af-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="355af-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="355af-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="355af-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="355af-106">Remarks</span></span>
<span data-ttu-id="355af-107">A `do` vazba se zobrazí, společně s nebo po `let` vazby, ale před definice člen v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="355af-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="355af-108">I když `do` – klíčové slovo je pro volitelné `do` vazby na úrovni modulu, není pro volitelné `do` vazby v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="355af-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="355af-109">Pro tvorbu každý objekt libovolného daného typu, nestatické `do` vazby a nestatické `let` vazby jsou spouštěny v pořadí, ve kterém se zobrazí v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="355af-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="355af-110">Více `do` vazby se může objevit v jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="355af-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="355af-111">Nestatické `let` vazby a nestatické `do` vazby stane textem primární konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="355af-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="355af-112">Kód v nestatickou `do` vazby části odkazovat primární konstruktor parametry a všechny hodnoty nebo funkce, které jsou definovány v `let` části vazby.</span><span class="sxs-lookup"><span data-stu-id="355af-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="355af-113">Nestatické `do` vazby můžete přístup ke členům třídy tak dlouho, dokud třída má vlastní identifikátor, který je definován `as` – klíčové slovo v třídě nadpis a pokud jsou všechny používá tyto členů kvalifikovaný pomocí vlastní identifikátor pro třídu.</span><span class="sxs-lookup"><span data-stu-id="355af-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="355af-114">Protože `let` vazby inicializovat soukromá pole třídy, který je často nutné zajistit, že členové chovat podle očekávání, `do` vazby jsou obvykle ukládat po `let` vazby, že kód `do` může vazby spustit s objektem plně inicializovaném.</span><span class="sxs-lookup"><span data-stu-id="355af-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="355af-115">Pokud váš kód se pokusí použít člen před dokončením inicializace, je vyvolána výjimkou InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="355af-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="355af-116">Statické `do` vazby mohou odkazovat statické členy nebo pole uzavření do třídy, ale není instance členů nebo pole.</span><span class="sxs-lookup"><span data-stu-id="355af-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="355af-117">Statické `do` vazby stane součástí statické inicializátoru pro třídu, která záruku, že se provést před prvním použití třídy.</span><span class="sxs-lookup"><span data-stu-id="355af-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="355af-118">Atributy jsou ignorovány pro `do` vazeb v typy.</span><span class="sxs-lookup"><span data-stu-id="355af-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="355af-119">Pokud atribut je požadován pro kód, který spustí `do` vazba, je nutné použít na primární konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="355af-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="355af-120">V následujícím kódu, třída má statického `do` vazby a nestatickou `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="355af-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="355af-121">Objekt nemá konstruktor, který má dva parametry `a` a `b`, a dva privátní pole jsou definovány v `let` vazby pro třídu.</span><span class="sxs-lookup"><span data-stu-id="355af-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="355af-122">Dvě vlastnosti je definována.</span><span class="sxs-lookup"><span data-stu-id="355af-122">Two properties are also defined.</span></span> <span data-ttu-id="355af-123">Všechny jsou v oboru v nestatickou `do` vazby části, jak je znázorněno použitím řádek, který vypíše všechny tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="355af-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="355af-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="355af-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="355af-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="355af-125">See Also</span></span>
[<span data-ttu-id="355af-126">Členové</span><span class="sxs-lookup"><span data-stu-id="355af-126">Members</span></span>](index.md)

[<span data-ttu-id="355af-127">Třídy</span><span class="sxs-lookup"><span data-stu-id="355af-127">Classes</span></span>](../classes.md)

[<span data-ttu-id="355af-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="355af-128">Constructors</span></span>](constructors.md)

[<span data-ttu-id="355af-129">`let` Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="355af-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="355af-130">`do` Vazby</span><span class="sxs-lookup"><span data-stu-id="355af-130">`do` Bindings</span></span>](../functions/do-Bindings.md)

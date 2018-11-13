---
title: Vazby do ve třídách (F#)
description: Další informace o použití jazyka F# udělat vazby v definici třídy, které provádí akce, když je objekt vytvořen nebo při prvním použití typu.
ms.date: 05/16/2016
ms.openlocfilehash: e54a5bde52bf6973cc338c929ba99e6fd5b53127
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43801521"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="55bcd-103">Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="55bcd-103">do Bindings in Classes</span></span>

<span data-ttu-id="55bcd-104">A `do` vazby v definici třídy provede akce při vytvoření objektu nebo pro statickou `do` vazby, když typ je nejprve použít.</span><span class="sxs-lookup"><span data-stu-id="55bcd-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="55bcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55bcd-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="55bcd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55bcd-106">Remarks</span></span>

<span data-ttu-id="55bcd-107">A `do` vazby se zobrazí spolu s nebo po `let` vazby, ale před definice členů v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="55bcd-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="55bcd-108">I když `do` – klíčové slovo je nepovinné pro `do` vazby na úrovni modulu není pro volitelné `do` vazby v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="55bcd-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="55bcd-109">Pro tvorbu žádné každý objekt daného typu, nestatické `do` vazby a informace o nestatická `let` vazby jsou provedeny v pořadí, v jakém jsou uvedeny v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="55bcd-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="55bcd-110">Více `do` vazby může dojít v jednom typu.</span><span class="sxs-lookup"><span data-stu-id="55bcd-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="55bcd-111">Nestatické `let` vazby a nestatické `do` vazby stát tělo primárnímu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="55bcd-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="55bcd-112">Kód v nestatické `do` část vazby můžete odkazovat na primární konstruktor parametry a hodnoty nebo funkce, které jsou definovány v `let` část vazby.</span><span class="sxs-lookup"><span data-stu-id="55bcd-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="55bcd-113">Nestatických `do` vazby můžete přistupovat k členům třídy, pokud třída má vlastní identifikátor, který je definován `as` – klíčové slovo ve třídě nadpis a dokud všechna použití těchto členů jsou kvalifikované identifikátoru samotného pro třídu.</span><span class="sxs-lookup"><span data-stu-id="55bcd-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="55bcd-114">Protože `let` vazby inicializovat privátní pole třídy, která je často nutné zajistit, že členové chovat dle očekávání, `do` vazby jsou obvykle umístěny po `let` vazby tak, že kód `do` může vazby Spusťte s plně inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="55bcd-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="55bcd-115">Pokud se váš kód se pokusí před dokončením inicializace, použijte člena, je vyvolána InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="55bcd-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="55bcd-116">Statické `do` vazby můžete odkazovat na statické členy nebo pole nadřazené třídy, ale není instancí členů nebo pole.</span><span class="sxs-lookup"><span data-stu-id="55bcd-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="55bcd-117">Statické `do` vazby se stanou součástí statický inicializátor pro třídu, která je zaručeno, že ke spuštění než třída při prvním použití.</span><span class="sxs-lookup"><span data-stu-id="55bcd-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="55bcd-118">Atributy se ignorují. pro `do` vazby v typech.</span><span class="sxs-lookup"><span data-stu-id="55bcd-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="55bcd-119">Pokud je požadované pro kód, který se spustí v atributu `do` vazby, musí být použita k primárnímu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="55bcd-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="55bcd-120">V následujícím kódu, že třída používá statickou `do` vazby a nestatická `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="55bcd-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="55bcd-121">Objekt nemá konstruktor, který má dva parametry `a` a `b`, a dvě soukromé pole jsou definována v `let` vazby pro třídu.</span><span class="sxs-lookup"><span data-stu-id="55bcd-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="55bcd-122">Dvě vlastnosti jsou také definovány.</span><span class="sxs-lookup"><span data-stu-id="55bcd-122">Two properties are also defined.</span></span> <span data-ttu-id="55bcd-123">Všechny z nich jsou v oboru v nestatické `do` část vazby, které jsou popsány v řádku, který vypíše všechny tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="55bcd-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="55bcd-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="55bcd-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="55bcd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55bcd-125">See also</span></span>

- [<span data-ttu-id="55bcd-126">Členové</span><span class="sxs-lookup"><span data-stu-id="55bcd-126">Members</span></span>](index.md)
- [<span data-ttu-id="55bcd-127">Třídy</span><span class="sxs-lookup"><span data-stu-id="55bcd-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="55bcd-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="55bcd-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="55bcd-129">`let` Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="55bcd-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="55bcd-130">`do` Vazby</span><span class="sxs-lookup"><span data-stu-id="55bcd-130">`do` Bindings</span></span>](../functions/do-Bindings.md)

---
title: Vazby do ve třídách
description: Naučte se používat F# vazbu do definice třídy, která provádí akce při vytváření objektu nebo při prvním použití typu.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627591"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="aa108-103">Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="aa108-103">do Bindings in Classes</span></span>

<span data-ttu-id="aa108-104">Vazba v definici třídy provádí akce, když je objekt vytvořen nebo, pro statickou `do` vazbu, při prvním použití typu. `do`</span><span class="sxs-lookup"><span data-stu-id="aa108-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa108-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa108-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="aa108-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa108-106">Remarks</span></span>

<span data-ttu-id="aa108-107">Vazba se zobrazí spolu s nebo po `let` vazbách, ale před definicemi členů v definici třídy. `do`</span><span class="sxs-lookup"><span data-stu-id="aa108-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="aa108-108">I když je `do` `do` klíčové slovo volitelné pro vazby na úrovni modulu, není volitelné pro vazby v definici třídy. `do`</span><span class="sxs-lookup"><span data-stu-id="aa108-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="aa108-109">Pro konstrukci každého objektu daného typu, nestatické `do` vazby a nestatické `let` vazby jsou spouštěny v pořadí, ve kterém jsou uvedeny v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="aa108-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="aa108-110">V `do` jednom typu může být více vazeb.</span><span class="sxs-lookup"><span data-stu-id="aa108-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="aa108-111">Nestatické `let` vazby a nestatické `do` vazby se stanou tělo primárního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="aa108-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="aa108-112">Kód v oddílu nestatické `do` vazby může odkazovat na parametry primárního konstruktoru a všechny hodnoty nebo funkce, které jsou definovány `let` v části Bindings.</span><span class="sxs-lookup"><span data-stu-id="aa108-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="aa108-113">Nestatické `do` vazby mají přístup ke členům třídy, pokud má vlastní identifikátor, který je definován `as` klíčovým slovem v záhlaví třídy, a pokud všechny použití těchto členů jsou kvalifikovány pomocí identifikátoru vlastníku pro třídu.</span><span class="sxs-lookup"><span data-stu-id="aa108-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="aa108-114">Vzhledem `let` k tomu, že vazby inicializují soukromá pole třídy, což je často nutné k zajištění toho, aby se členové `do` chovali podle očekávání, `let` vazby jsou obvykle umístěny po vazbách tak, aby kód ve `do` vazbě mohl provede se plně inicializovaným objektem.</span><span class="sxs-lookup"><span data-stu-id="aa108-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="aa108-115">Pokud se váš kód pokusí použít člena před dokončením inicializace, dojde k vyvolání InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="aa108-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="aa108-116">Statické `do` vazby můžou odkazovat na statické členy nebo pole ohraničující třídy, ale ne členy instance nebo pole.</span><span class="sxs-lookup"><span data-stu-id="aa108-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="aa108-117">Statické `do` vazby se stanou součástí statického inicializátoru pro třídu, která je zaručena k provedení před prvním použitím třídy.</span><span class="sxs-lookup"><span data-stu-id="aa108-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="aa108-118">Atributy jsou u `do` vazeb v typech ignorovány.</span><span class="sxs-lookup"><span data-stu-id="aa108-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="aa108-119">Pokud je vyžadován atribut pro kód, který je spuštěn ve `do` vazbě, je nutné použít na primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="aa108-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="aa108-120">V následujícím kódu má třída statickou `do` vazbu a nestatickou `do` vazbu.</span><span class="sxs-lookup"><span data-stu-id="aa108-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="aa108-121">Objekt má konstruktor, který má dva parametry `a` a `b`a dvě soukromá `let` pole jsou definována ve vazbách pro třídu.</span><span class="sxs-lookup"><span data-stu-id="aa108-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="aa108-122">Jsou definované také dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa108-122">Two properties are also defined.</span></span> <span data-ttu-id="aa108-123">Všechny tyto položky jsou v rozsahu v sekci nestatické `do` vazby, jak je znázorněno na řádku, který tiskne všechny tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aa108-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="aa108-124">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="aa108-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="aa108-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa108-125">See also</span></span>

- [<span data-ttu-id="aa108-126">Členové</span><span class="sxs-lookup"><span data-stu-id="aa108-126">Members</span></span>](index.md)
- [<span data-ttu-id="aa108-127">Třídy</span><span class="sxs-lookup"><span data-stu-id="aa108-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="aa108-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="aa108-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="aa108-129">`let`Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="aa108-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="aa108-130">`do`Vazeb</span><span class="sxs-lookup"><span data-stu-id="aa108-130">`do` Bindings</span></span>](../functions/do-Bindings.md)

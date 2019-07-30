---
title: Vazby let ve třídách
description: Naučte se definovat soukromá pole a soukromé funkce pro F# třídy pomocí vazeb let v definici třídy.
ms.date: 05/16/2016
ms.openlocfilehash: 0086d3a91f85395c2bd0555f978c5d951c363357
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627480"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="d341d-103">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="d341d-103">let Bindings in Classes</span></span>

<span data-ttu-id="d341d-104">Můžete definovat soukromá pole a soukromé funkce pro F# třídy pomocí `let` vazeb v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d341d-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="d341d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d341d-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="d341d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d341d-106">Remarks</span></span>

<span data-ttu-id="d341d-107">Předchozí syntaxe se zobrazí za záhlavím třídy a deklaracemi dědičnosti, ale před jakýmikoli definicemi členů.</span><span class="sxs-lookup"><span data-stu-id="d341d-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="d341d-108">Syntaxe je stejná jako u `let` vazeb mimo třídy, ale názvy definované ve třídě mají obor, který je omezen na třídu.</span><span class="sxs-lookup"><span data-stu-id="d341d-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="d341d-109">`let` Vazba vytvoří soukromé pole nebo funkci; k veřejnému vystavení dat nebo funkcí, deklaraci vlastnosti nebo metody člena.</span><span class="sxs-lookup"><span data-stu-id="d341d-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="d341d-110">Vazba, která není statická, se nazývá vazba instance `let`. `let`</span><span class="sxs-lookup"><span data-stu-id="d341d-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="d341d-111">Vazby `let` instance jsou spouštěny při vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="d341d-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="d341d-112">Statické `let` vazby jsou součástí statického inicializátoru pro třídu, která je zaručena k provedení před prvním použitím typu.</span><span class="sxs-lookup"><span data-stu-id="d341d-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="d341d-113">Kód v rámci vazeb `let` instance může používat parametry primárního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d341d-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="d341d-114">Atributy a Modifikátory dostupnosti nejsou u `let` vazeb ve třídách povoleny.</span><span class="sxs-lookup"><span data-stu-id="d341d-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="d341d-115">Následující příklady kódu ilustrují několik typů `let` vazeb ve třídách.</span><span class="sxs-lookup"><span data-stu-id="d341d-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="d341d-116">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="d341d-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="d341d-117">Alternativní způsoby vytváření polí</span><span class="sxs-lookup"><span data-stu-id="d341d-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="d341d-118">`val` Klíčové slovo můžete také použít k vytvoření soukromého pole.</span><span class="sxs-lookup"><span data-stu-id="d341d-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="d341d-119">Při použití `val` klíčového slova není pole při vytvoření objektu přidělena hodnota, ale místo toho je inicializována s výchozí hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d341d-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="d341d-120">Další informace najdete v tématu [explicitní pole: Klíčové slovo](explicit-fields-the-val-keyword.md)Val</span><span class="sxs-lookup"><span data-stu-id="d341d-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="d341d-121">Můžete také definovat soukromá pole ve třídě pomocí definice člena a přidat klíčové slovo `private` do definice.</span><span class="sxs-lookup"><span data-stu-id="d341d-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="d341d-122">To může být užitečné, pokud očekáváte, že změníte přístupnost člena, aniž byste museli přepisovat kód.</span><span class="sxs-lookup"><span data-stu-id="d341d-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="d341d-123">Další informace najdete v tématu [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="d341d-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d341d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d341d-124">See also</span></span>

- [<span data-ttu-id="d341d-125">Členové</span><span class="sxs-lookup"><span data-stu-id="d341d-125">Members</span></span>](index.md)
- [<span data-ttu-id="d341d-126">`do`Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="d341d-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="d341d-127">`let`Vazeb</span><span class="sxs-lookup"><span data-stu-id="d341d-127">`let` Bindings</span></span>](../functions/let-bindings.md)

---
title: Vazby let ve třídách (F#)
description: "Zjistěte, jak definovat privátním polím a privátní funkce pro třídy F # pomocí vazby, umožní' v definici třídy."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="b3e31-103">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="b3e31-103">let Bindings in Classes</span></span>

<span data-ttu-id="b3e31-104">Můžete definovat privátním polím a privátní funkce pro třídy F # pomocí `let` vazby v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="b3e31-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="b3e31-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3e31-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="b3e31-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3e31-106">Remarks</span></span>
<span data-ttu-id="b3e31-107">Předchozí syntaxe se zobrazí po deklaracích záhlaví a dědičnost třídy, ale před všechny definice člen.</span><span class="sxs-lookup"><span data-stu-id="b3e31-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="b3e31-108">Syntaxe je stejná jako u `let` vazby mimo třídy, ale názvy definované v třídě mít obor, který je omezený na třídu.</span><span class="sxs-lookup"><span data-stu-id="b3e31-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="b3e31-109">A `let` vazbou soukromé pole nebo funkce; ke zveřejňování dat nebo funkce deklarovat veřejně, vlastnost nebo metoda člen.</span><span class="sxs-lookup"><span data-stu-id="b3e31-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="b3e31-110">A `let` vazby, který není statický nazývá instance `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="b3e31-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="b3e31-111">Instance `let` vazby spuštění při vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="b3e31-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="b3e31-112">Statické `let` vazby jsou součástí statické inicializátoru pro třídu, která záruku, že se provést před prvním použití typu.</span><span class="sxs-lookup"><span data-stu-id="b3e31-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="b3e31-113">Kód v rámci instance `let` vazby můžete použít primární konstruktor parametry.</span><span class="sxs-lookup"><span data-stu-id="b3e31-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="b3e31-114">Atributy a usnadnění modifikátory nejsou povolené pro `let` vazby do ve třídách.</span><span class="sxs-lookup"><span data-stu-id="b3e31-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="b3e31-115">Následující příklady kódu ilustrují několik typů `let` vazby do ve třídách.</span><span class="sxs-lookup"><span data-stu-id="b3e31-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="b3e31-116">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="b3e31-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="b3e31-117">Alternativní způsoby, jak vytvořit pole</span><span class="sxs-lookup"><span data-stu-id="b3e31-117">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="b3e31-118">Můžete také `val` – klíčové slovo k vytvoření soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="b3e31-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="b3e31-119">Při použití `val` – klíčové slovo, pole není zadána hodnota, pokud objekt se vytvoří, ale místo toho se inicializuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b3e31-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="b3e31-120">Další informace najdete v tématu [explicitní pole: val – klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="b3e31-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="b3e31-121">Můžete také definovat privátním polím v třídě pomocí definice člena a přidáním klíčové slovo `private` k definici.</span><span class="sxs-lookup"><span data-stu-id="b3e31-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="b3e31-122">To může být užitečné, pokud očekáváte, chcete-li změnit usnadnění člena bez přepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="b3e31-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="b3e31-123">Další informace najdete v tématu [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="b3e31-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e31-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3e31-124">See Also</span></span>
[<span data-ttu-id="b3e31-125">Členové</span><span class="sxs-lookup"><span data-stu-id="b3e31-125">Members</span></span>](index.md)

[<span data-ttu-id="b3e31-126">`do` Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="b3e31-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="b3e31-127">`let` Vazby</span><span class="sxs-lookup"><span data-stu-id="b3e31-127">`let` Bindings</span></span>](../functions/let-bindings.md)

---
title: "Vazby let ve třídách (F#)"
description: "Zjistěte, jak definovat privátním polím a privátní funkce pro třídy F # pomocí vazby, umožní' v definici třídy."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="1c4fc-104">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="1c4fc-104">let Bindings in Classes</span></span>

<span data-ttu-id="1c4fc-105">Můžete definovat privátním polím a privátní funkce pro třídy F # pomocí `let` vazby v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-105">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="1c4fc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c4fc-106">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="1c4fc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c4fc-107">Remarks</span></span>
<span data-ttu-id="1c4fc-108">Předchozí syntaxe se zobrazí po deklaracích záhlaví a dědičnost třídy, ale před všechny definice člen.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-108">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="1c4fc-109">Syntaxe je stejná jako u `let` vazby mimo třídy, ale názvy definované v třídě mít obor, který je omezený na třídu.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-109">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="1c4fc-110">A `let` vazbou soukromé pole nebo funkce; ke zveřejňování dat nebo funkce deklarovat veřejně, vlastnost nebo metoda člen.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-110">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="1c4fc-111">A `let` vazby, který není statický nazývá instance `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-111">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="1c4fc-112">Instance `let` vazby spuštění při vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-112">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="1c4fc-113">Statické `let` vazby jsou součástí statické inicializátoru pro třídu, která záruku, že se provést před prvním použití typu.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-113">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="1c4fc-114">Kód v rámci instance `let` vazby můžete použít primární konstruktor parametry.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-114">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="1c4fc-115">Atributy a usnadnění modifikátory nejsou povolené pro `let` vazby do ve třídách.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-115">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="1c4fc-116">Následující příklady kódu ilustrují několik typů `let` vazby do ve třídách.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-116">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="1c4fc-117">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-117">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="1c4fc-118">Alternativní způsoby, jak vytvořit pole</span><span class="sxs-lookup"><span data-stu-id="1c4fc-118">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="1c4fc-119">Můžete také `val` – klíčové slovo k vytvoření soukromé pole.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-119">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="1c4fc-120">Při použití `val` – klíčové slovo, pole není zadána hodnota, pokud objekt se vytvoří, ale místo toho se inicializuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-120">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="1c4fc-121">Další informace najdete v tématu [explicitní pole: val – klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="1c4fc-121">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="1c4fc-122">Můžete také definovat privátním polím v třídě pomocí definice člena a přidáním klíčové slovo `private` k definici.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-122">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="1c4fc-123">To může být užitečné, pokud očekáváte, chcete-li změnit usnadnění člena bez přepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="1c4fc-123">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="1c4fc-124">Další informace najdete v tématu [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="1c4fc-124">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c4fc-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c4fc-125">See Also</span></span>
[<span data-ttu-id="1c4fc-126">Členy</span><span class="sxs-lookup"><span data-stu-id="1c4fc-126">Members</span></span>](index.md)

[<span data-ttu-id="1c4fc-127">`do`Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="1c4fc-127">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="1c4fc-128">`let`Vazby</span><span class="sxs-lookup"><span data-stu-id="1c4fc-128">`let` Bindings</span></span>](../functions/let-bindings.md)

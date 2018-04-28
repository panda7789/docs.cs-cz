---
title: Objektové výrazy (F#)
description: 'Naučte se používat objektové výrazy F # Pokud chcete, aby se zabránilo další kód a režijní náklady na potřebné pro vytvoření nové, s názvem typu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f5a728823e7abe18aeb604b3991087fd0252698e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="object-expressions"></a><span data-ttu-id="4d0a5-103">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="4d0a5-103">Object Expressions</span></span>

<span data-ttu-id="4d0a5-104">*Objektu výraz* je výraz, který vytvoří novou instanci typu dynamicky vytvořený, anonymní objekt, který je založen na existující základní typ, rozhraní nebo sadu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="4d0a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d0a5-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="4d0a5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d0a5-106">Remarks</span></span>
<span data-ttu-id="4d0a5-107">V předchozích syntaxi *typename* představuje existující typu třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="4d0a5-108">*parametry typu* popisuje parametry volitelné obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="4d0a5-109">*Argumenty* se používají pouze pro typy tříd, které vyžadují parametry konstruktor.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="4d0a5-110">*Člen definice* přepsání metody třídy base nebo implementace metod abstraktní základní třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="4d0a5-111">Následující příklad ukazuje několik různých typů objektové výrazy.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="4d0a5-112">Použitím objektových výrazů</span><span class="sxs-lookup"><span data-stu-id="4d0a5-112">Using Object Expressions</span></span>
<span data-ttu-id="4d0a5-113">Objektové výrazy používají, když budete chtít vyhnout navíc kód a režijní náklady, který je potřeba vytvořit novou, s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="4d0a5-114">Pokud používáte objektové výrazy minimalizovat počet typy vytvořené v programu, můžete snížit počet řádků kódu a zabránit zbytečné rozšíření typy.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="4d0a5-115">Místo vytváření mnoho typů pouze pro zpracování konkrétních situacích, můžete použít objekt výraz, který upravuje existující typ nebo poskytuje odpovídající implementace rozhraní pro konkrétní případ po ruce.</span><span class="sxs-lookup"><span data-stu-id="4d0a5-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="4d0a5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d0a5-116">See Also</span></span>
[<span data-ttu-id="4d0a5-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="4d0a5-117">F# Language Reference</span></span>](index.md)

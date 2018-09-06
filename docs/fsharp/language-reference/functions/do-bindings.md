---
title: do – vazby (F#)
description: 'Zjistěte, jak jazyka F # udělat vazby se používá k provádění kódu bez definování funkce nebo hodnota.'
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882730"
---
# <a name="do-bindings"></a><span data-ttu-id="893a6-103">do – vazby</span><span class="sxs-lookup"><span data-stu-id="893a6-103">do Bindings</span></span>

<span data-ttu-id="893a6-104">A `do` vazby se používá k provádění kódu bez definování funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="893a6-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="893a6-105">Také proveďte vazby může být použit ve třídách, naleznete v tématu [ `do` vazby ve třídách](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="893a6-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="893a6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="893a6-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="893a6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="893a6-107">Remarks</span></span>

<span data-ttu-id="893a6-108">Použití `do` vazby, pokud chcete spustit kód bez ohledu na jejich definici funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="893a6-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="893a6-109">Výraz v `do` vazby musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="893a6-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="893a6-110">Kód v nejvyšší úrovni `do` vazby je proveden při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="893a6-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="893a6-111">Klíčové slovo `do` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="893a6-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="893a6-112">Atributy lze použít na nejvyšší úrovni `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="893a6-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="893a6-113">Například pokud program používá zprostředkovatele komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašemu programu.</span><span class="sxs-lookup"><span data-stu-id="893a6-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="893a6-114">Můžete to provést pomocí atributu na `do` vazbu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="893a6-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="893a6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="893a6-115">See also</span></span>

- [<span data-ttu-id="893a6-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="893a6-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="893a6-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="893a6-117">Functions</span></span>](index.md)

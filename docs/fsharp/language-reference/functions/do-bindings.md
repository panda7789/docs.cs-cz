---
title: "do – vazby (F#)"
description: "Zjistěte, jak F # \"do\" vazby se používá ke spouštění kódu bez definování funkce nebo hodnota."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="bb058-104">do – vazby</span><span class="sxs-lookup"><span data-stu-id="bb058-104">do Bindings</span></span>

<span data-ttu-id="bb058-105">A `do` vazby se používá ke spouštění kódu bez definování funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="bb058-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="bb058-106">Proveďte vazby může být také používány třídy, najdete v části [ `do` vazby do ve třídách](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="bb058-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="bb058-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb058-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="bb058-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb058-108">Remarks</span></span>
<span data-ttu-id="bb058-109">Použití `do` vazby, pokud chcete spustit kód s nezávisle na definici funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="bb058-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="bb058-110">Výraz v `do` vazby musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="bb058-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="bb058-111">Kód nejvyšší úrovni `do` vazba se spustí při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="bb058-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="bb058-112">Klíčové slovo `do` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="bb058-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="bb058-113">Atributy lze použít jako nejvyšší úrovni `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="bb058-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="bb058-114">Například pokud váš program používá zprostředkovatel komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="bb058-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="bb058-115">Můžete to provést pomocí atributu na `do` vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="bb058-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="bb058-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb058-116">See Also</span></span>
[<span data-ttu-id="bb058-117">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="bb058-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="bb058-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="bb058-118">Functions</span></span>](index.md)


---
title: do – vazby (F#)
description: 'Zjistěte, jak F # "do" vazby se používá ke spouštění kódu bez definování funkce nebo hodnota.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="do-bindings"></a><span data-ttu-id="61c7b-103">do – vazby</span><span class="sxs-lookup"><span data-stu-id="61c7b-103">do Bindings</span></span>

<span data-ttu-id="61c7b-104">A `do` vazby se používá ke spouštění kódu bez definování funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="61c7b-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="61c7b-105">Proveďte vazby může být také používány třídy, najdete v části [ `do` vazby do ve třídách](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="61c7b-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="61c7b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61c7b-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="61c7b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61c7b-107">Remarks</span></span>
<span data-ttu-id="61c7b-108">Použití `do` vazby, pokud chcete spustit kód s nezávisle na definici funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="61c7b-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="61c7b-109">Výraz v `do` vazby musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="61c7b-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="61c7b-110">Kód nejvyšší úrovni `do` vazba se spustí při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="61c7b-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="61c7b-111">Klíčové slovo `do` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="61c7b-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="61c7b-112">Atributy lze použít jako nejvyšší úrovni `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="61c7b-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="61c7b-113">Například pokud váš program používá zprostředkovatel komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="61c7b-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="61c7b-114">Můžete to provést pomocí atributu na `do` vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="61c7b-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="61c7b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="61c7b-115">See Also</span></span>
[<span data-ttu-id="61c7b-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="61c7b-116">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="61c7b-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="61c7b-117">Functions</span></span>](index.md)


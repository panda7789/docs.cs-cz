---
title: do – vazby
description: Zjistěte, jak F# "do" vazby se používá k provádění kódu bez definování funkce nebo hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: 0755e36912fc4e5a645e55eb4bee5c730a56cadf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641918"
---
# <a name="do-bindings"></a><span data-ttu-id="638bd-103">do – vazby</span><span class="sxs-lookup"><span data-stu-id="638bd-103">do Bindings</span></span>

<span data-ttu-id="638bd-104">A `do` vazby se používá k provádění kódu bez definování funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="638bd-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="638bd-105">Také proveďte vazby může být použit ve třídách, naleznete v tématu [ `do` vazby ve třídách](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="638bd-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="638bd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638bd-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="638bd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="638bd-107">Remarks</span></span>

<span data-ttu-id="638bd-108">Použití `do` vazby, pokud chcete spustit kód bez ohledu na jejich definici funkce nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="638bd-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="638bd-109">Výraz v `do` vazby musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="638bd-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="638bd-110">Kód v nejvyšší úrovni `do` vazby je proveden při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="638bd-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="638bd-111">Klíčové slovo `do` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="638bd-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="638bd-112">Atributy lze použít na nejvyšší úrovni `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="638bd-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="638bd-113">Například pokud program používá zprostředkovatele komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašemu programu.</span><span class="sxs-lookup"><span data-stu-id="638bd-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="638bd-114">Můžete to provést pomocí atributu na `do` vazbu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="638bd-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="638bd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="638bd-115">See also</span></span>

- [<span data-ttu-id="638bd-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="638bd-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="638bd-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="638bd-117">Functions</span></span>](index.md)

---
title: do – vazby
description: Zjistěte, jak F# se vazba do používá ke spouštění kódu bez definování funkce nebo hodnoty.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630537"
---
# <a name="do-bindings"></a><span data-ttu-id="25333-103">do – vazby</span><span class="sxs-lookup"><span data-stu-id="25333-103">do Bindings</span></span>

<span data-ttu-id="25333-104">`do` Vazba se používá ke spouštění kódu bez definování funkce nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25333-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="25333-105">Vazby do třídy lze také použít ve třídách naleznete v tématu [ `do` Bindings in Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="25333-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="25333-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25333-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="25333-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25333-107">Remarks</span></span>

<span data-ttu-id="25333-108">`do` Použijte vazbu, pokud chcete spustit kód nezávisle na definici funkce nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25333-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="25333-109">Výraz ve `do` vazbě musí vracet `unit`.</span><span class="sxs-lookup"><span data-stu-id="25333-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="25333-110">Kód v vazbě nejvyšší úrovně `do` se spustí při inicializaci modulu.</span><span class="sxs-lookup"><span data-stu-id="25333-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="25333-111">Klíčové slovo `do` je volitelné.</span><span class="sxs-lookup"><span data-stu-id="25333-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="25333-112">Atributy lze použít na vazbu nejvyšší úrovně `do` .</span><span class="sxs-lookup"><span data-stu-id="25333-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="25333-113">Například pokud váš program používá zprostředkovatele komunikace s objekty COM, může být vhodné použít `STAThread` atribut pro váš program.</span><span class="sxs-lookup"><span data-stu-id="25333-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="25333-114">Můžete to provést pomocí atributu u `do` vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="25333-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="25333-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25333-115">See also</span></span>

- [<span data-ttu-id="25333-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="25333-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="25333-117">Funkce</span><span class="sxs-lookup"><span data-stu-id="25333-117">Functions</span></span>](index.md)

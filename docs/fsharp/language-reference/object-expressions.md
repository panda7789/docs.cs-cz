---
title: Objektové výrazy
description: Další informace o použití F# objektové výrazy, když chcete se vyhnout zvláštní kód a režijní náklady na potřebné k vytvoření nového, s názvem typu.
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666284"
---
# <a name="object-expressions"></a><span data-ttu-id="1544d-103">Objektové výrazy</span><span class="sxs-lookup"><span data-stu-id="1544d-103">Object Expressions</span></span>

<span data-ttu-id="1544d-104">*Objektu výraz* je výraz, který vytvoří novou instanci typu dynamicky generovaný anonymní objekt, který je založen na existující základní typ, rozhraní nebo sady rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1544d-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="1544d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1544d-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="1544d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1544d-106">Remarks</span></span>

<span data-ttu-id="1544d-107">V předchozí syntaxi *typename* představuje existující typu třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1544d-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="1544d-108">*parametry typu* obsahuje popis parametrů, volitelné obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1544d-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="1544d-109">*Argumenty* se používají pouze pro typy tříd, které vyžadují parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1544d-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="1544d-110">*Definice členů* přepsání metody základní třídy nebo implementace abstraktní metody ze základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1544d-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="1544d-111">Následující příklad ukazuje několik různých typů objektové výrazy.</span><span class="sxs-lookup"><span data-stu-id="1544d-111">The following example illustrates several different types of object expressions.</span></span>

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="1544d-112">Použitím objektových výrazů</span><span class="sxs-lookup"><span data-stu-id="1544d-112">Using Object Expressions</span></span>

<span data-ttu-id="1544d-113">Objektové výrazy používají, když chcete se vyhnout zvláštní kód a režijní náklady, který je potřeba vytvořit nový s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="1544d-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="1544d-114">Používáte-li minimalizovat počet typů, které jsou vytvořené v programu objektové výrazy, můžete snížit počet řádků kódu a zabránit zbytečným růst počtu typů.</span><span class="sxs-lookup"><span data-stu-id="1544d-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="1544d-115">Místo vytváření mnoho typů pouze pro zpracování konkrétních situacích, můžete použít objektový výraz, který přizpůsobí existujícího typu nebo poskytuje ve vhodné implementaci rozhraní pro tento konkrétní případ po ruce.</span><span class="sxs-lookup"><span data-stu-id="1544d-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="1544d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1544d-116">See also</span></span>

- [<span data-ttu-id="1544d-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1544d-117">F# Language Reference</span></span>](index.md)

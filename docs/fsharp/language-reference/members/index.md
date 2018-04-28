---
title: Členy (F#)
description: 'Další informace o objektu členy v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a37f14d138cc017cf78e3a0ff1d5b5bba2f09020
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="members"></a><span data-ttu-id="9da2a-103">Členové</span><span class="sxs-lookup"><span data-stu-id="9da2a-103">Members</span></span>

<span data-ttu-id="9da2a-104">Tato část popisuje členy typy objektů F #.</span><span class="sxs-lookup"><span data-stu-id="9da2a-104">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="9da2a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9da2a-105">Remarks</span></span>
<span data-ttu-id="9da2a-106">*Členové* jsou funkce, které jsou součástí definice typu a jsou deklarovány s `member` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9da2a-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="9da2a-107">Objekt typů F # například záznamy, třídy, rozlišované sjednocení, rozhraní, a struktury podporují členy.</span><span class="sxs-lookup"><span data-stu-id="9da2a-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="9da2a-108">Další informace najdete v tématu [záznamy](../records.md), [třídy](../classes.md), [Rozlišované sjednocení](../discriminated-Unions.md), [rozhraní](../interfaces.md), a [struktury](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="9da2a-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="9da2a-109">Členové obvykle tvoří veřejné rozhraní pro typ, který je důvod, proč jsou veřejné, pokud není uvedeno jinak.</span><span class="sxs-lookup"><span data-stu-id="9da2a-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="9da2a-110">Členy lze deklarovat také soukromý nebo interní.</span><span class="sxs-lookup"><span data-stu-id="9da2a-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="9da2a-111">Další informace najdete v tématu [řízení přístupu](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="9da2a-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="9da2a-112">Podpisy pro typy lze také vystavit nebo není odhalí určité členy typu.</span><span class="sxs-lookup"><span data-stu-id="9da2a-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="9da2a-113">Další informace najdete v tématu [podpisy](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="9da2a-113">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="9da2a-114">Soukromé pole a `do` vazby, které se používají pouze s třídami, nejsou členy hodnotu true, protože nikdy jsou součástí veřejného rozhraní typu a nejsou deklarovat s `member` – klíčové slovo, ale jsou popsané v této části taky.</span><span class="sxs-lookup"><span data-stu-id="9da2a-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="9da2a-115">Související témata</span><span class="sxs-lookup"><span data-stu-id="9da2a-115">Related Topics</span></span>


|<span data-ttu-id="9da2a-116">Téma</span><span class="sxs-lookup"><span data-stu-id="9da2a-116">Topic</span></span>|<span data-ttu-id="9da2a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9da2a-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="9da2a-118">`let` Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="9da2a-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="9da2a-119">Popisuje definice privátní pole a funkce ve třídách.</span><span class="sxs-lookup"><span data-stu-id="9da2a-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="9da2a-120">`do` Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="9da2a-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="9da2a-121">Popisuje specifikace kód inicializace objektu.</span><span class="sxs-lookup"><span data-stu-id="9da2a-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="9da2a-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9da2a-122">Properties</span></span>](properties.md)|<span data-ttu-id="9da2a-123">Popisuje vlastnost členy v třídami a ostatními typy.</span><span class="sxs-lookup"><span data-stu-id="9da2a-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="9da2a-124">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9da2a-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="9da2a-125">Popisuje vlastnosti jako pole v třídami a ostatními typy.</span><span class="sxs-lookup"><span data-stu-id="9da2a-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="9da2a-126">Metody</span><span class="sxs-lookup"><span data-stu-id="9da2a-126">Methods</span></span>](methods.md)|<span data-ttu-id="9da2a-127">Popisuje funkce, které jsou členy typu.</span><span class="sxs-lookup"><span data-stu-id="9da2a-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="9da2a-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9da2a-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="9da2a-129">Popisuje speciální funkce, které inicializovat objekty typu.</span><span class="sxs-lookup"><span data-stu-id="9da2a-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="9da2a-130">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="9da2a-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="9da2a-131">Popisuje definice přizpůsobené operátory pro typy.</span><span class="sxs-lookup"><span data-stu-id="9da2a-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="9da2a-132">Události</span><span class="sxs-lookup"><span data-stu-id="9da2a-132">Events</span></span>](events.md)|<span data-ttu-id="9da2a-133">Popisuje definice události a události zpracování podpory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="9da2a-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="9da2a-134">Explicitní pole: Klíčové slovo `val`</span><span class="sxs-lookup"><span data-stu-id="9da2a-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="9da2a-135">Popisuje definice Neinicializovaný pole v typu.</span><span class="sxs-lookup"><span data-stu-id="9da2a-135">Describes the definition of uninitialized fields in a type.</span></span>|

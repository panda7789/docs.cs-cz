---
title: Členy (F#)
description: 'Další informace o objektu členy v programovací jazyk F #.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="b8bef-104">Členové</span><span class="sxs-lookup"><span data-stu-id="b8bef-104">Members</span></span>

<span data-ttu-id="b8bef-105">Tato část popisuje členy typy objektů F #.</span><span class="sxs-lookup"><span data-stu-id="b8bef-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="b8bef-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8bef-106">Remarks</span></span>
<span data-ttu-id="b8bef-107">*Členové* jsou funkce, které jsou součástí definice typu a jsou deklarovány s `member` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b8bef-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="b8bef-108">Objekt typů F # například záznamy, třídy, rozlišované sjednocení, rozhraní, a struktury podporují členy.</span><span class="sxs-lookup"><span data-stu-id="b8bef-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="b8bef-109">Další informace najdete v tématu [záznamy](../records.md), [třídy](../classes.md), [Rozlišované sjednocení](../discriminated-Unions.md), [rozhraní](../interfaces.md), a [struktury](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="b8bef-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="b8bef-110">Členové obvykle tvoří veřejné rozhraní pro typ, který je důvod, proč jsou veřejné, pokud není uvedeno jinak.</span><span class="sxs-lookup"><span data-stu-id="b8bef-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="b8bef-111">Členy lze deklarovat také soukromý nebo interní.</span><span class="sxs-lookup"><span data-stu-id="b8bef-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="b8bef-112">Další informace najdete v tématu [řízení přístupu](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="b8bef-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="b8bef-113">Podpisy pro typy lze také vystavit nebo není odhalí určité členy typu.</span><span class="sxs-lookup"><span data-stu-id="b8bef-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="b8bef-114">Další informace najdete v tématu [podpisy](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="b8bef-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="b8bef-115">Soukromé pole a `do` vazby, které se používají pouze s třídami, nejsou členy hodnotu true, protože nikdy jsou součástí veřejného rozhraní typu a nejsou deklarovat s `member` – klíčové slovo, ale jsou popsané v této části taky.</span><span class="sxs-lookup"><span data-stu-id="b8bef-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="b8bef-116">Související témata</span><span class="sxs-lookup"><span data-stu-id="b8bef-116">Related Topics</span></span>


|<span data-ttu-id="b8bef-117">Téma</span><span class="sxs-lookup"><span data-stu-id="b8bef-117">Topic</span></span>|<span data-ttu-id="b8bef-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b8bef-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="b8bef-119">`let`Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="b8bef-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="b8bef-120">Popisuje definice privátní pole a funkce ve třídách.</span><span class="sxs-lookup"><span data-stu-id="b8bef-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="b8bef-121">`do`Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="b8bef-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="b8bef-122">Popisuje specifikace kód inicializace objektu.</span><span class="sxs-lookup"><span data-stu-id="b8bef-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="b8bef-123">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b8bef-123">Properties</span></span>](properties.md)|<span data-ttu-id="b8bef-124">Popisuje vlastnost členy v třídami a ostatními typy.</span><span class="sxs-lookup"><span data-stu-id="b8bef-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="b8bef-125">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b8bef-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="b8bef-126">Popisuje vlastnosti jako pole v třídami a ostatními typy.</span><span class="sxs-lookup"><span data-stu-id="b8bef-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="b8bef-127">Metody</span><span class="sxs-lookup"><span data-stu-id="b8bef-127">Methods</span></span>](methods.md)|<span data-ttu-id="b8bef-128">Popisuje funkce, které jsou členy typu.</span><span class="sxs-lookup"><span data-stu-id="b8bef-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="b8bef-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="b8bef-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="b8bef-130">Popisuje speciální funkce, které inicializovat objekty typu.</span><span class="sxs-lookup"><span data-stu-id="b8bef-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="b8bef-131">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="b8bef-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="b8bef-132">Popisuje definice přizpůsobené operátory pro typy.</span><span class="sxs-lookup"><span data-stu-id="b8bef-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="b8bef-133">Události</span><span class="sxs-lookup"><span data-stu-id="b8bef-133">Events</span></span>](events.md)|<span data-ttu-id="b8bef-134">Popisuje definice události a události zpracování podpory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="b8bef-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="b8bef-135">Explicitní pole: `val` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="b8bef-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="b8bef-136">Popisuje definice Neinicializovaný pole v typu.</span><span class="sxs-lookup"><span data-stu-id="b8bef-136">Describes the definition of uninitialized fields in a type.</span></span>|

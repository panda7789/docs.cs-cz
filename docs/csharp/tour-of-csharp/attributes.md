---
title: C# atributy - přehled používání jazyka C#
description: Další informace o deklarativní programování pomocí atributů v jazyce C#
keywords: Rozhraní .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="ddbc1-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="ddbc1-104">Attributes</span></span>

<span data-ttu-id="ddbc1-105">Typy, členů a ostatní entity v programu v C# podporovat modifikátory, které řídí některé aspekty jejich chování.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="ddbc1-106">Například usnadnění metody je řízena pomocí `public`, `protected`, `internal`, a `private` modifikátory.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="ddbc1-107">C# umožňuje zobecnit této funkci tak, aby uživatelem definované typy deklarativní informací lze připojit k programu entity a načítat za běhu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="ddbc1-108">Programy zadejte tyto informace další deklarativní definice a používání ***atributy***.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="ddbc1-109">Následující příklad deklaruje `HelpAttribute` atribut, který je možné použít u entity program poskytnout odkazy na jejich související dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="ddbc1-110">Všechny třídy atributů odvozena od <xref:System.Attribute> základní třída poskytuje standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="ddbc1-111">Tím, že jejich jména, společně s všechny argumenty uvnitř hranaté závorky těsně před přidružené deklaraci, můžete použít atributů.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="ddbc1-112">Pokud název atributu končí na `Attribute`, tuto část názvu lze vynechat, když je atribut.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="ddbc1-113">Například `HelpAttribute` atributu je možné následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="ddbc1-114">Tento příklad se připojí `HelpAttribute` k `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="ddbc1-115">Přidá další `HelpAttribute` k `Display` metodu v třídě.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="ddbc1-116">Veřejné konstruktory atribut třídy řídit informace, které je třeba zadat při atribut je připojen k programu entity.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="ddbc1-117">Další informace se dá zajistit pod položkou veřejné vlastnosti třídy atributů pro čtení a zápis (například odkaz na `Topic` vlastnost dříve).</span><span class="sxs-lookup"><span data-stu-id="ddbc1-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="ddbc1-118">Vyžádání konkrétní atribut prostřednictvím reflexe v konstruktoru pro třídy atributů vyvolání informací uvedených v programu zdroj a se vrátí výsledný instance atributu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="ddbc1-119">Pokud Další informace se poskytovaly prostřednictvím vlastnosti, tyto vlastnosti jsou nastaveny na dané hodnoty před vrácením instance atributu.</span><span class="sxs-lookup"><span data-stu-id="ddbc1-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="ddbc1-120">Předchozí</span><span class="sxs-lookup"><span data-stu-id="ddbc1-120">Previous</span></span>](delegates.md)

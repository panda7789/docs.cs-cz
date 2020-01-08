---
title: C#Rozhraní – prohlídka C# jazyka
description: Rozhraní definují smlouvy implementované typy vC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: d10d9f69cebe9a05cdff9b9ff5d817237bf8c56f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346831"
---
# <a name="interfaces"></a><span data-ttu-id="335a5-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="335a5-103">Interfaces</span></span>

<span data-ttu-id="335a5-104">***Rozhraní*** definuje kontrakt, který může být implementován pomocí tříd a struktur.</span><span class="sxs-lookup"><span data-stu-id="335a5-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="335a5-105">Rozhraní může obsahovat metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="335a5-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="335a5-106">Rozhraní neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="335a5-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="335a5-107">Rozhraní mohou využívat ***vícenásobnou dědičnost***.</span><span class="sxs-lookup"><span data-stu-id="335a5-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="335a5-108">V následujícím příkladu rozhraní `IComboBox` dědí z `ITextBox` a `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="335a5-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="335a5-109">Třídy a struktury mohou implementovat více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="335a5-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="335a5-110">V následujícím příkladu třída `EditBox` implementuje `IControl` a `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="335a5-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="335a5-111">Pokud třída nebo struktura implementuje konkrétní rozhraní, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="335a5-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="335a5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="335a5-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="335a5-113">V případech, kdy instance není staticky známá pro implementaci konkrétního rozhraní, lze použít dynamické přetypování typu.</span><span class="sxs-lookup"><span data-stu-id="335a5-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="335a5-114">Například následující příkazy používají přetypování dynamického typu k získání `IControl` a `IDataBound` rozhraní objektu.</span><span class="sxs-lookup"><span data-stu-id="335a5-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="335a5-115">Vzhledem k tomu, že je skutečný typ objektu run-time `EditBox`, přetypování je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="335a5-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="335a5-116">V předchozí třídě `EditBox` jsou implementovány `Paint` metoda z rozhraní `IControl` a metoda `Bind` z rozhraní `IDataBound` pomocí veřejných členů.</span><span class="sxs-lookup"><span data-stu-id="335a5-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="335a5-117">C#podporuje také explicitní ***implementace členů rozhraní***, což umožňuje třídě nebo struktuře zabránit členům Public.</span><span class="sxs-lookup"><span data-stu-id="335a5-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="335a5-118">Explicitní implementace člena rozhraní je zapsána pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="335a5-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="335a5-119">Například třída `EditBox` by mohla implementovat metody `IControl.Paint` a `IDataBound.Bind` pomocí explicitních implementací členů rozhraní následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="335a5-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="335a5-120">K explicitním členům rozhraní lze přistupovat pouze prostřednictvím typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="335a5-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="335a5-121">Například implementace `IControl.Paint` poskytovaná předchozí třídou EditBox lze vyvolat pouze první převod `EditBox` odkaz na typ rozhraní `IControl`.</span><span class="sxs-lookup"><span data-stu-id="335a5-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="335a5-122">[Předchozí](arrays.md)
>[Další](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="335a5-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>

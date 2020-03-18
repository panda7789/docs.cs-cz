---
title: Rozhraní Jazyka C# – prohlídka jazyka C#
description: 'Rozhraní definují smlouvy implementované typy v C #'
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159127"
---
# <a name="interfaces"></a><span data-ttu-id="1b57d-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b57d-103">Interfaces</span></span>

<span data-ttu-id="1b57d-104">***Rozhraní*** definuje smlouvu, která může být implementována třídami a strukturami.</span><span class="sxs-lookup"><span data-stu-id="1b57d-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="1b57d-105">Rozhraní může obsahovat metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="1b57d-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="1b57d-106">Rozhraní neposkytuje implementace členů, které definuje – pouze určuje členy, které musí být dodány třídy nebo struktury, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-106">An interface doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="1b57d-107">Rozhraní mohou využívat ***více dědičnosti***.</span><span class="sxs-lookup"><span data-stu-id="1b57d-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="1b57d-108">V následujícím příkladu `IComboBox` rozhraní dědí `ITextBox` `IListBox`z obou a .</span><span class="sxs-lookup"><span data-stu-id="1b57d-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="1b57d-109">Třídy a struktury mohou implementovat více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="1b57d-110">V následujícím příkladu `EditBox` třída implementuje oba `IControl` a `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="1b57d-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="1b57d-111">Když třída nebo struktura implementuje určité rozhraní, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="1b57d-112">Například</span><span class="sxs-lookup"><span data-stu-id="1b57d-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="1b57d-113">V případech, kdy instance není staticky známo, že implementovat určité rozhraní, dynamický typ přetypovádá lze použít.</span><span class="sxs-lookup"><span data-stu-id="1b57d-113">In cases where an instance isn't statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="1b57d-114">Například následující příkazy používají přetypové dynamické typy `IControl` `IDataBound` k získání implementace objektu a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="1b57d-115">Vzhledem k tomu, že skutečný `EditBox`typ objektu za běhu je , přetypová tažné období úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1b57d-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="1b57d-116">V předchozí `EditBox` třídě `Paint` metoda z `IControl` rozhraní `Bind` a metoda `IDataBound` z rozhraní jsou implementovány pomocí veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="1b57d-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="1b57d-117">C# také podporuje explicitní implementace členů rozhraní , povolení ***třídy***nebo struktury, aby se zabránilo vytváření členů veřejnosti.</span><span class="sxs-lookup"><span data-stu-id="1b57d-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="1b57d-118">Explicitní implementace člena rozhraní je zapsána pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="1b57d-119">Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metody pomocí explicitní implementace členů rozhraní takto.</span><span class="sxs-lookup"><span data-stu-id="1b57d-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="1b57d-120">Explicitní členové rozhraní lze přistupovat pouze prostřednictvím typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="1b57d-121">Například implementaci `IControl.Paint` poskytuje předchozí EditBox třídy lze vyvolat pouze nejprve `EditBox` převést `IControl` odkaz na typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b57d-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="1b57d-122">[Předchozí](arrays.md)
>[další](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="1b57d-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>

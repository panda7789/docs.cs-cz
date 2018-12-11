---
title: C#Rozhraní – připravuje C# jazyka
description: Definování kontraktů implementovaných typů v rozhraníC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144114"
---
# <a name="interfaces"></a><span data-ttu-id="72271-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="72271-103">Interfaces</span></span>

<span data-ttu-id="72271-104">***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="72271-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="72271-105">Rozhraní může obsahovat metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="72271-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="72271-106">Rozhraní neposkytuje implementace členů definuje – pouze Určuje členy, které je třeba dodat ze třídy nebo struktury, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="72271-107">Rozhraní může využívat ***vícenásobná dědičnost***.</span><span class="sxs-lookup"><span data-stu-id="72271-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="72271-108">V následujícím příkladu, rozhraní `IComboBox` zdědí vlastnosti z obou `ITextBox` a `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="72271-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="72271-109">Třídy a struktury mohou implementovat více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="72271-110">V následujícím příkladu třída `EditBox` implementuje oba `IControl` a `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="72271-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="72271-111">Pokud konkrétní rozhraní implementuje, třídy nebo struktury, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="72271-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="72271-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="72271-113">V případech, kde není instance znám staticky implementovat určité rozhraní je možné dynamického přetypování.</span><span class="sxs-lookup"><span data-stu-id="72271-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="72271-114">Například následující příkazy použijte k získání objektu dynamického přetypování `IControl` a `IDataBound` implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="72271-115">Protože je za běhu skutečný typ objektu `EditBox`, úspěšné položky CAST.</span><span class="sxs-lookup"><span data-stu-id="72271-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="72271-116">V předchozím `EditBox` třídy, `Paint` metodu z `IControl` rozhraní a `Bind` metodu z `IDataBound` rozhraní jsou implementovány pomocí veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="72271-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="72271-117">C#také podporuje explicitní ***implementace členů rozhraní***, povolení dané třídy nebo struktury předejděte tomu, aby veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="72271-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="72271-118">Implementace explicitního rozhraní člen je zapsáno s použitím rozhraní plně kvalifikovaný název člena.</span><span class="sxs-lookup"><span data-stu-id="72271-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="72271-119">Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metod pomocí explicitní implementace členů rozhraní následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="72271-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="72271-120">Explicitní rozhraní členy jsou přístupné pouze prostřednictvím typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="72271-121">Například provádění `IControl.Paint` zadaný podle předchozí EditBox třídy lze vyvolat pouze první převedením `EditBox` odkaz `IControl` typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="72271-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="72271-122">[Předchozí](arrays.md)
>[další](enums.md)</span><span class="sxs-lookup"><span data-stu-id="72271-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
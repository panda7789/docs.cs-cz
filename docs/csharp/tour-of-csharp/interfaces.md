---
title: "Rozhraní jazyka C# – přehled používání jazyka C#"
description: "Rozhraní definovat kontrakty implementované typy v jazyku C#"
keywords: "Rozhraní .NET, csharp, rozhraní, vícenásobná dědičnost polymorfismus"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="18f89-104">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="18f89-104">Interfaces</span></span>

<span data-ttu-id="18f89-105">***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="18f89-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="18f89-106">Rozhraní může obsahovat metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="18f89-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="18f89-107">Rozhraní neposkytuje implementace členů definuje – jenom určuje členů, které je nutné zadat třídy nebo struktury, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18f89-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="18f89-108">Rozhraní mohou využívat ***vícenásobná dědičnost***.</span><span class="sxs-lookup"><span data-stu-id="18f89-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="18f89-109">V následujícím příkladu, rozhraní `IComboBox` zdědí vlastnosti z obou `ITextBox` a `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="18f89-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="18f89-110">Třídy a struktury můžete implementovat více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18f89-110">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="18f89-111">V následujícím příkladu třída `EditBox` implementuje obě `IControl` a `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="18f89-111">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="18f89-112">Při třídě nebo struktuře implementuje určité rozhraní, může instance této třídě nebo struktuře implicitně převést na tento typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18f89-112">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="18f89-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="18f89-113">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="18f89-114">V případech, kde instance nezná staticky implementovat určité rozhraní můžete použít dynamický typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="18f89-114">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="18f89-115">Například následující příkazy použít dynamický typ přetypování k získání objektu `IControl` a `IDataBound` rozhraní implementace.</span><span class="sxs-lookup"><span data-stu-id="18f89-115">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="18f89-116">Protože je skutečný typ spuštění objektu `EditBox`, položky CAST úspěšné.</span><span class="sxs-lookup"><span data-stu-id="18f89-116">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="18f89-117">V předchozím `EditBox` třídy, `Paint` metoda z `IControl` rozhraní a `Bind` metoda z `IDataBound` rozhraní jsou implementované pomocí veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="18f89-117">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="18f89-118">C# také podporuje explicitní ***rozhraní implementace členských***, povolení třídě nebo struktuře vyhnout se provádění veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="18f89-118">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="18f89-119">Implementace explicitního rozhraní člen je vytvořené pomocí rozhraní plně kvalifikovaný název člena.</span><span class="sxs-lookup"><span data-stu-id="18f89-119">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="18f89-120">Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metod pomocí explicitní rozhraní implementace členských následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="18f89-120">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="18f89-121">Členové explicitní rozhraní jsou přístupné pouze prostřednictvím typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18f89-121">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="18f89-122">Například implementace `IControl.Paint` zadaný podle předchozích textového pole třídu jde volat jenom první převedením `EditBox` odkaz na `IControl` typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18f89-122">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="18f89-123">[Předchozí](arrays.md)
[další](enums.md)</span><span class="sxs-lookup"><span data-stu-id="18f89-123">[Previous](arrays.md)
[Next](enums.md)</span></span>

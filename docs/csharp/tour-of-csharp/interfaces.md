---
title: Rozhraní jazyka C# – přehled používání jazyka C#
description: Rozhraní definovat kontrakty implementované typy v jazyku C#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343892"
---
# <a name="interfaces"></a><span data-ttu-id="cdee8-103">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdee8-103">Interfaces</span></span>

<span data-ttu-id="cdee8-104">***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="cdee8-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="cdee8-105">Rozhraní může obsahovat metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="cdee8-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="cdee8-106">Rozhraní neposkytuje implementace členů definuje – jenom určuje členů, které je nutné zadat třídy nebo struktury, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdee8-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="cdee8-107">Rozhraní mohou využívat ***vícenásobná dědičnost***.</span><span class="sxs-lookup"><span data-stu-id="cdee8-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="cdee8-108">V následujícím příkladu, rozhraní `IComboBox` zdědí vlastnosti z obou `ITextBox` a `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="cdee8-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="cdee8-109">Třídy a struktury můžete implementovat více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdee8-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="cdee8-110">V následujícím příkladu třída `EditBox` implementuje obě `IControl` a `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="cdee8-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="cdee8-111">Při třídě nebo struktuře implementuje určité rozhraní, může instance této třídě nebo struktuře implicitně převést na tento typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdee8-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="cdee8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdee8-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="cdee8-113">V případech, kde instance nezná staticky implementovat určité rozhraní můžete použít dynamický typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="cdee8-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="cdee8-114">Například následující příkazy použít dynamický typ přetypování k získání objektu `IControl` a `IDataBound` rozhraní implementace.</span><span class="sxs-lookup"><span data-stu-id="cdee8-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="cdee8-115">Protože je skutečný typ spuštění objektu `EditBox`, položky CAST úspěšné.</span><span class="sxs-lookup"><span data-stu-id="cdee8-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="cdee8-116">V předchozím `EditBox` třídy, `Paint` metoda z `IControl` rozhraní a `Bind` metoda z `IDataBound` rozhraní jsou implementované pomocí veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="cdee8-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="cdee8-117">C# také podporuje explicitní ***rozhraní implementace členských***, povolení třídě nebo struktuře vyhnout se provádění veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="cdee8-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="cdee8-118">Implementace explicitního rozhraní člen je vytvořené pomocí rozhraní plně kvalifikovaný název člena.</span><span class="sxs-lookup"><span data-stu-id="cdee8-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="cdee8-119">Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metod pomocí explicitní rozhraní implementace členských následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cdee8-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="cdee8-120">Členové explicitní rozhraní jsou přístupné pouze prostřednictvím typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdee8-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="cdee8-121">Například implementace `IControl.Paint` zadaný podle předchozích textového pole třídu jde volat jenom první převedením `EditBox` odkaz na `IControl` typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cdee8-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="cdee8-122">[Předchozí](arrays.md)
[další](enums.md)</span><span class="sxs-lookup"><span data-stu-id="cdee8-122">[Previous](arrays.md)
[Next](enums.md)</span></span>

---
title: Indexery v rozhraních – Průvodce programováním v C#
description: Indexery lze deklarovat v rozhraní v jazyce C#. Přečtěte si, jak se přístupové objekty indexerů rozhraní liší od přístupových objektů indexerů tříd.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303098"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="396e0-104">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="396e0-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="396e0-105">Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="396e0-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="396e0-106">Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="396e0-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="396e0-107">Přistupující objekty rozhraní nepoužívají modifikátory.</span><span class="sxs-lookup"><span data-stu-id="396e0-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="396e0-108">Přistupující objekt rozhraní nemá obvykle tělo.</span><span class="sxs-lookup"><span data-stu-id="396e0-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="396e0-109">Účelem přístupového objektu je určit, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="396e0-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="396e0-110">Můžete zadat implementaci indexeru definovaného v rozhraní, ale to je vzácné.</span><span class="sxs-lookup"><span data-stu-id="396e0-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="396e0-111">Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="396e0-112">Následuje příklad přístupového objektu indexeru rozhraní:</span><span class="sxs-lookup"><span data-stu-id="396e0-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="396e0-113">Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="396e0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="396e0-114">Example</span></span>

<span data-ttu-id="396e0-115">Následující příklad ukazuje, jak implementovat indexery rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="396e0-116">V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="396e0-117">Například</span><span class="sxs-lookup"><span data-stu-id="396e0-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="396e0-118">Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru.</span><span class="sxs-lookup"><span data-stu-id="396e0-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="396e0-119">Například pokud `Employee` Třída implementuje dvě rozhraní `ICitizen` a a `IEmployee` obě rozhraní mají stejný podpis indexeru, je nutné implementovat explicitní implementaci člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="396e0-120">To znamená následující deklaraci indexeru:</span><span class="sxs-lookup"><span data-stu-id="396e0-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="396e0-121">implementuje indexer na `IEmployee` rozhraní a následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="396e0-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="396e0-122">implementuje indexer na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="396e0-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="396e0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="396e0-123">See also</span></span>

- [<span data-ttu-id="396e0-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="396e0-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="396e0-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="396e0-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="396e0-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="396e0-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="396e0-127">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="396e0-127">Interfaces</span></span>](../interfaces/index.md)

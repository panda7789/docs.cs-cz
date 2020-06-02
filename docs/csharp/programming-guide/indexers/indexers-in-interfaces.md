---
title: Indexery v rozhraních – Průvodce programováním v C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 9ce6e4f0e0533c2880c6241f44409435248a336a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287477"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="67180-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="67180-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="67180-103">Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="67180-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="67180-104">Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="67180-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="67180-105">Přistupující objekty rozhraní nepoužívají modifikátory.</span><span class="sxs-lookup"><span data-stu-id="67180-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="67180-106">Přistupující objekt rozhraní nemá obvykle tělo.</span><span class="sxs-lookup"><span data-stu-id="67180-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="67180-107">Účelem přístupového objektu je určit, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="67180-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="67180-108">Můžete zadat implementaci indexeru definovaného v rozhraní, ale to je vzácné.</span><span class="sxs-lookup"><span data-stu-id="67180-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="67180-109">Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="67180-110">Následuje příklad přístupového objektu indexeru rozhraní:</span><span class="sxs-lookup"><span data-stu-id="67180-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="67180-111">Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="67180-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="67180-112">Example</span></span>

<span data-ttu-id="67180-113">Následující příklad ukazuje, jak implementovat indexery rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="67180-114">V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="67180-115">Například</span><span class="sxs-lookup"><span data-stu-id="67180-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="67180-116">Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru.</span><span class="sxs-lookup"><span data-stu-id="67180-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="67180-117">Například pokud `Employee` Třída implementuje dvě rozhraní `ICitizen` a a `IEmployee` obě rozhraní mají stejný podpis indexeru, je nutné implementovat explicitní implementaci člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="67180-118">To znamená následující deklaraci indexeru:</span><span class="sxs-lookup"><span data-stu-id="67180-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="67180-119">implementuje indexer na `IEmployee` rozhraní a následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="67180-119">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="67180-120">implementuje indexer na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67180-120">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="67180-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="67180-121">See also</span></span>

- [<span data-ttu-id="67180-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="67180-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="67180-123">Indexery</span><span class="sxs-lookup"><span data-stu-id="67180-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="67180-124">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="67180-124">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="67180-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="67180-125">Interfaces</span></span>](../interfaces/index.md)

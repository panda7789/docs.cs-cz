---
title: Indexery v rozhraních – programovací příručka Jazyka C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627835"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="897bb-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="897bb-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="897bb-103">Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="897bb-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="897bb-104">Přístupové servery indexerů rozhraní se liší od přístupových modulů indexerů [třídy](../../language-reference/keywords/class.md) následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="897bb-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="897bb-105">Přístupové moduly rozhraní nepoužívají modifikátory.</span><span class="sxs-lookup"><span data-stu-id="897bb-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="897bb-106">Přístupový objekt rozhraní obvykle nemá tělo.</span><span class="sxs-lookup"><span data-stu-id="897bb-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="897bb-107">Účelem přistupujícího serveru je označit, zda indexer je jen pro čtení, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="897bb-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="897bb-108">Můžete poskytnout implementaci pro indexer definované v rozhraní, ale to je vzácné.</span><span class="sxs-lookup"><span data-stu-id="897bb-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="897bb-109">Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="897bb-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="897bb-110">Následuje příklad přístupového objektu indexeru rozhraní:</span><span class="sxs-lookup"><span data-stu-id="897bb-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="897bb-111">Podpis indexeru se musí lišit od podpisů všech ostatních indexerů deklarovaných ve stejném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="897bb-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="897bb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="897bb-112">Example</span></span>

<span data-ttu-id="897bb-113">Následující příklad ukazuje, jak implementovat indexery rozhraní.</span><span class="sxs-lookup"><span data-stu-id="897bb-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="897bb-114">V předchozím příkladu můžete použít implementaci explicitního člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="897bb-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="897bb-115">Například</span><span class="sxs-lookup"><span data-stu-id="897bb-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="897bb-116">Plně kvalifikovaný název je však potřeba pouze zabránit nejednoznačnosti, když třída implementuje více než jedno rozhraní se stejným podpisem indexeru.</span><span class="sxs-lookup"><span data-stu-id="897bb-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="897bb-117">Například pokud `Employee` třída implementuje dvě `ICitizen` rozhraní `IEmployee`a , a obě rozhraní mají stejný podpis indexeru, explicitní implementace člena rozhraní je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="897bb-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="897bb-118">To znamená následující prohlášení indexeru:</span><span class="sxs-lookup"><span data-stu-id="897bb-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="897bb-119">implementuje indexer `ICitizen` na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="897bb-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="897bb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="897bb-120">See also</span></span>

- [<span data-ttu-id="897bb-121">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="897bb-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="897bb-122">Indexery</span><span class="sxs-lookup"><span data-stu-id="897bb-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="897bb-123">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="897bb-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="897bb-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="897bb-124">Interfaces</span></span>](../interfaces/index.md)

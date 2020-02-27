---
title: Indexery v rozhraních C# – Průvodce programováním
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627835"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="64044-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="64044-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="64044-103">Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="64044-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="64044-104">Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="64044-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="64044-105">Přistupující objekty rozhraní nepoužívají modifikátory.</span><span class="sxs-lookup"><span data-stu-id="64044-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="64044-106">Přistupující objekt rozhraní nemá obvykle tělo.</span><span class="sxs-lookup"><span data-stu-id="64044-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="64044-107">Účelem přístupového objektu je určit, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="64044-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="64044-108">Můžete zadat implementaci indexeru definovaného v rozhraní, ale to je vzácné.</span><span class="sxs-lookup"><span data-stu-id="64044-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="64044-109">Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="64044-110">Následuje příklad přístupového objektu indexeru rozhraní:</span><span class="sxs-lookup"><span data-stu-id="64044-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="64044-111">Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="64044-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="64044-112">Example</span></span>

<span data-ttu-id="64044-113">Následující příklad ukazuje, jak implementovat indexery rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="64044-114">V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="64044-115">Například</span><span class="sxs-lookup"><span data-stu-id="64044-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="64044-116">Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru.</span><span class="sxs-lookup"><span data-stu-id="64044-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="64044-117">Například pokud třída `Employee` implementuje dvě rozhraní, `ICitizen` a `IEmployee`a obě rozhraní mají stejný podpis indexeru, je nutná implementace explicitního člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="64044-118">To znamená následující deklaraci indexeru:</span><span class="sxs-lookup"><span data-stu-id="64044-118">That is, the following indexer declaration:</span></span>

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

<span data-ttu-id="64044-119">implementuje indexer na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64044-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="64044-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="64044-120">See also</span></span>

- [<span data-ttu-id="64044-121">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="64044-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="64044-122">Indexery</span><span class="sxs-lookup"><span data-stu-id="64044-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="64044-123">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="64044-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="64044-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="64044-124">Interfaces</span></span>](../interfaces/index.md)

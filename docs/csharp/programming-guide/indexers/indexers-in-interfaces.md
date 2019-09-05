---
title: Indexery v rozhraních C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 7f52df0283cf057c1cd6cc4fa87c0086da7e61d2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253007"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="49771-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="49771-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="49771-103">Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="49771-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="49771-104">Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="49771-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="49771-105">Přistupující objekty rozhraní nepoužívají modifikátory.</span><span class="sxs-lookup"><span data-stu-id="49771-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="49771-106">Přistupující objekt rozhraní nemá tělo.</span><span class="sxs-lookup"><span data-stu-id="49771-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="49771-107">Proto je účel přístupového objektu označovat, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="49771-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="49771-108">Následuje příklad přístupového objektu indexeru rozhraní:</span><span class="sxs-lookup"><span data-stu-id="49771-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="49771-109">Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49771-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49771-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="49771-110">Example</span></span>  
 <span data-ttu-id="49771-111">Následující příklad ukazuje, jak implementovat indexery rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49771-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="49771-112">V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49771-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="49771-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="49771-113">For example:</span></span>  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="49771-114">Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru.</span><span class="sxs-lookup"><span data-stu-id="49771-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="49771-115">Například pokud `Employee` třída implementuje dvě `ICitizen` rozhraní a `IEmployee`a obě rozhraní mají stejný podpis indexeru, je nutné implementovat explicitní implementaci člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49771-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="49771-116">To znamená následující deklaraci indexeru:</span><span class="sxs-lookup"><span data-stu-id="49771-116">That is, the following indexer declaration:</span></span>  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="49771-117">implementuje indexer na `IEmployee` rozhraní a následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="49771-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="49771-118">implementuje indexer na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49771-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49771-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49771-119">See also</span></span>

- [<span data-ttu-id="49771-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49771-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="49771-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="49771-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="49771-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="49771-122">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="49771-123">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="49771-123">Interfaces</span></span>](../interfaces/index.md)

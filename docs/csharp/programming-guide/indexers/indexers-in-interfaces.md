---
title: Indexery v rozhraní - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c56369b28f8e1bab1ca8e8c13ebd9710c8f1d9fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679827"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="c37a2-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c37a2-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="c37a2-103">Indexery mohou být deklarovány na [rozhraní](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="c37a2-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="c37a2-104">Přistupující objekty rozhraní indexery se liší od přístupových objektů [třídy](../../../csharp/language-reference/keywords/class.md) indexery následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="c37a2-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="c37a2-105">Přístupové objekty rozhraní nepoužívejte modifikátory.</span><span class="sxs-lookup"><span data-stu-id="c37a2-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="c37a2-106">Přístupový objekt rozhraní nemá tělo.</span><span class="sxs-lookup"><span data-stu-id="c37a2-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="c37a2-107">Účelem přístupového objektu je proto udává, jestli je indexeru pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="c37a2-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="c37a2-108">Následuje příklad rozhraní indexeru přístupového objektu:</span><span class="sxs-lookup"><span data-stu-id="c37a2-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="c37a2-109">Podpis indexeru se musí lišit od podpisů ze všech indexerů je deklarována v stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c37a2-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c37a2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c37a2-110">Example</span></span>  
 <span data-ttu-id="c37a2-111">Následující příklad ukazuje, jak implementovat rozhraní indexery.</span><span class="sxs-lookup"><span data-stu-id="c37a2-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="c37a2-112">V předchozím příkladu můžete použít explicitní implementace členu rozhraní s použitím plně kvalifikovaný název tohoto člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c37a2-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="c37a2-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c37a2-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="c37a2-114">Plně kvalifikovaný název je však potřeba jenom k třída implementuje víc než jedno rozhraní se stejným podpisem indexer-li předejít nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="c37a2-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="c37a2-115">Například pokud `Employee` třída implementuje dvě rozhraní, `ICitizen` a `IEmployee`, a obě rozhraní mají stejnou signaturu indexer, je nutné explicitní implementace členu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c37a2-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="c37a2-116">To znamená, následující deklarace indexer:</span><span class="sxs-lookup"><span data-stu-id="c37a2-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="c37a2-117">implementuje indexer na `IEmployee` rozhraní při následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="c37a2-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="c37a2-118">implementuje indexer na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c37a2-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37a2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c37a2-119">See also</span></span>

- [<span data-ttu-id="c37a2-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c37a2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c37a2-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="c37a2-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="c37a2-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c37a2-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="c37a2-123">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c37a2-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

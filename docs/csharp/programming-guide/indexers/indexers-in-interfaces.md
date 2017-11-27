---
title: "Indexery v rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 304f2e037d8df025376d06f229ddd1584f8713b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="b2ec1-102">Indexery v rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b2ec1-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="b2ec1-103">Indexery lze deklarovat na [rozhraní](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="b2ec1-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="b2ec1-104">Přístupové objekty z rozhraní indexery se liší od přístupových objektů [třída](../../../csharp/language-reference/keywords/class.md) indexery následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="b2ec1-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="b2ec1-105">Přístupové objekty rozhraní nepoužívejte modifikátory.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="b2ec1-106">Přistupující objekt rozhraní nemá text.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="b2ec1-107">Účelem přistupujícího objektu je proto označuje, zda indexeru pro čtení a zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="b2ec1-108">Následuje příklad přistupující objekt indexer rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b2ec1-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="b2ec1-109">Podpis indexer se musí lišit od signatur jinými indexery deklarovaným ve stejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2ec1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2ec1-110">Example</span></span>  
 <span data-ttu-id="b2ec1-111">Následující příklad ukazuje, jak implementovat rozhraní indexery.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="b2ec1-112">V předchozím příkladu můžete použít člen implementace explicitního rozhraní pomocí plně kvalifikovaný název člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="b2ec1-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b2ec1-113">For example:</span></span>  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 <span data-ttu-id="b2ec1-114">Plně kvalifikovaný název je však potřeba jenom aby se zabránilo nejednoznačnosti, když třída je implementace více než jedno rozhraní se stejným podpisem indexer.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="b2ec1-115">Například pokud `Employee` třída je implementace dvě rozhraní, `ICitizen` a `IEmployee`, a obě rozhraní mají stejným podpisem indexer člen implementace explicitního rozhraní je nutné.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="b2ec1-116">To znamená, následující prohlášení indexer:</span><span class="sxs-lookup"><span data-stu-id="b2ec1-116">That is, the following indexer declaration:</span></span>  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 <span data-ttu-id="b2ec1-117">implementuje indexeru na `IEmployee` rozhraní při následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="b2ec1-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 <span data-ttu-id="b2ec1-118">implementuje indexeru na `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b2ec1-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ec1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2ec1-119">See Also</span></span>  
 [<span data-ttu-id="b2ec1-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b2ec1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2ec1-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="b2ec1-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="b2ec1-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b2ec1-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="b2ec1-123">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2ec1-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

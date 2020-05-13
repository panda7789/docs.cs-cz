---
title: Selektivní serializace
description: V tomto článku se dozvíte, jak označit pole pomocí neserializovaného atributu, který brání v serializaci pole.
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: c7203c4ea13c65f8d88c55de96988d3b1d9e9611
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379164"
---
# <a name="selective-serialization"></a><span data-ttu-id="656c8-103">Selektivní serializace</span><span class="sxs-lookup"><span data-stu-id="656c8-103">Selective serialization</span></span>
<span data-ttu-id="656c8-104">Třída často obsahuje pole, která by neměla být serializována.</span><span class="sxs-lookup"><span data-stu-id="656c8-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="656c8-105">Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="656c8-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="656c8-106">Při deserializaci třídy vlákno uloženo ID pro, když byla třída serializována, již pravděpodobně není spuštěna; Proto serializace této hodnoty nemá smysl.</span><span class="sxs-lookup"><span data-stu-id="656c8-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="656c8-107">Můžete zabránit serializaci členských proměnných jejich označením pomocí [Neserializovaného](xref:System.NonSerializedAttribute) atributu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="656c8-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="656c8-108">Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="656c8-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="656c8-109">Pokud objekt musí být serializován, použijte `NonSerialized` atribut pro konkrétní pole, která ukládají citlivá data.</span><span class="sxs-lookup"><span data-stu-id="656c8-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="656c8-110">Pokud tato pole nevylučujete ze serializace, uvědomte si, že data, která jsou uložena, jsou vystavena jakémukoli kódu, který má oprávnění k serializaci.</span><span class="sxs-lookup"><span data-stu-id="656c8-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="656c8-111">Další informace o psaní kódu zabezpečené serializace naleznete v tématu [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="656c8-111">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="656c8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="656c8-112">See also</span></span>

- [<span data-ttu-id="656c8-113">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="656c8-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="656c8-114">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="656c8-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="656c8-115">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="656c8-115">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)

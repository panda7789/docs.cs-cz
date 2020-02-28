---
title: Selektivní serializace
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: cc5d7964d5f3268f08721593fefc07e3eff853ca
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159595"
---
# <a name="selective-serialization"></a><span data-ttu-id="aef75-102">Selektivní serializace</span><span class="sxs-lookup"><span data-stu-id="aef75-102">Selective serialization</span></span>
<span data-ttu-id="aef75-103">Třída často obsahuje pole, která by neměla být serializována.</span><span class="sxs-lookup"><span data-stu-id="aef75-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="aef75-104">Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="aef75-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="aef75-105">Při deserializaci třídy vlákno uloženo ID pro, když byla třída serializována, již pravděpodobně není spuštěna; Proto serializace této hodnoty nemá smysl.</span><span class="sxs-lookup"><span data-stu-id="aef75-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="aef75-106">Můžete zabránit serializaci členských proměnných jejich označením pomocí [Neserializovaného](xref:System.NonSerializedAttribute) atributu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="aef75-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="aef75-107">Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aef75-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="aef75-108">Pokud objekt musí být serializován, použijte atribut `NonSerialized` pro konkrétní pole, která ukládají citlivá data.</span><span class="sxs-lookup"><span data-stu-id="aef75-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="aef75-109">Pokud tato pole nevylučujete ze serializace, uvědomte si, že data, která jsou uložena, jsou vystavena jakémukoli kódu, který má oprávnění k serializaci.</span><span class="sxs-lookup"><span data-stu-id="aef75-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="aef75-110">Další informace o psaní kódu zabezpečené serializace naleznete v tématu [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="aef75-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="aef75-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="aef75-111">See also</span></span>

- [<span data-ttu-id="aef75-112">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="aef75-112">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="aef75-113">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="aef75-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="aef75-114">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="aef75-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)

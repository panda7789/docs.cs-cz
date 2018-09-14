---
title: Selektivní serializace
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: 74e21045ec70faf6ee82200a15362d51edf61433
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513497"
---
# <a name="selective-serialization"></a><span data-ttu-id="831c2-102">Selektivní serializace</span><span class="sxs-lookup"><span data-stu-id="831c2-102">Selective serialization</span></span>
<span data-ttu-id="831c2-103">Třída často obsahuje pole, která nesmí být serializován.</span><span class="sxs-lookup"><span data-stu-id="831c2-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="831c2-104">Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="831c2-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="831c2-105">Když je deserializovat třídu, vlákno uloží ID pro kdy byl serializován třída může již být spuštěn; tak serializaci tato hodnota nemá smysl.</span><span class="sxs-lookup"><span data-stu-id="831c2-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="831c2-106">Proměnné členů mohou zabránit serializována jejich označením [NonSerialized](xref:System.NonSerializedAttribute) atribut následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="831c2-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="831c2-107">Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="831c2-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="831c2-108">Pokud objekt musí být serializován, použije `NonSerialized` atribut konkrétní pole, které ukládat citlivá data.</span><span class="sxs-lookup"><span data-stu-id="831c2-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="831c2-109">Pokud tato pole není vyloučit z serializace, mějte na paměti, že jsou data, která jsou v nich uložené vystavena jakýkoli kód, který má oprávnění k serializaci.</span><span class="sxs-lookup"><span data-stu-id="831c2-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="831c2-110">Další informace o psaní kódu zabezpečené serializace naleznete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="831c2-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="831c2-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="831c2-111">See also</span></span>

- [<span data-ttu-id="831c2-112">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="831c2-112">Binary Serialization</span></span>](binary-serialization.md)  
- [<span data-ttu-id="831c2-113">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="831c2-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
- [<span data-ttu-id="831c2-114">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="831c2-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)

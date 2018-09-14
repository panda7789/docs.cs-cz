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
# <a name="selective-serialization"></a>Selektivní serializace
Třída často obsahuje pole, která nesmí být serializován. Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné. Když je deserializovat třídu, vlákno uloží ID pro kdy byl serializován třída může již být spuštěn; tak serializaci tato hodnota nemá smysl. Proměnné členů mohou zabránit serializována jejich označením [NonSerialized](xref:System.NonSerializedAttribute) atribut následujícím způsobem.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení. Pokud objekt musí být serializován, použije `NonSerialized` atribut konkrétní pole, které ukládat citlivá data. Pokud tato pole není vyloučit z serializace, mějte na paměti, že jsou data, která jsou v nich uložené vystavena jakýkoli kód, který má oprávnění k serializaci. Další informace o psaní kódu zabezpečené serializace naleznete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také:

- [Binární serializace](binary-serialization.md)  
- [Serializace XML a SOAP](xml-and-soap-serialization.md)  
- [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)

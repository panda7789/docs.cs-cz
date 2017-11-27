---
title: "Selektivní serializace"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a>Selektivní serializace
Třída často obsahuje pole, která nesmí být serializován. Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné. Pokud je třída deserializovat, vlákno uložené ID pro když byl serializován třída můžou už běžet; proto serializaci tato hodnota nemá smysl. Členské proměnné můžete zabránit jejich s označením serializována [NonSerialized](xref:System.NonSerializedAttribute) atribut následujícím způsobem.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení. Pokud objekt musí být serializované, budou použity `NonSerialized` atribut konkrétních polí, které obsahují citlivá data. Pokud tato pole není vyloučit z serializace, mějte na paměti, které uchovávají data jsou viditelné na kód, který má oprávnění k serializaci. Další informace o psaní kódu Zabezpečte Serializační najdete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také  
 [Binární serializace](binary-serialization.md)  
 [XML a serializace protokolu SOAP](xml-and-soap-serialization.md)  
 [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)
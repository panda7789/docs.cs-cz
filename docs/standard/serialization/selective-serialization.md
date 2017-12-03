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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf1c585a171f2842084c1fdce639e479ce5ca8d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
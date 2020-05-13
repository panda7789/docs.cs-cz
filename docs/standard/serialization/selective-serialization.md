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
# <a name="selective-serialization"></a>Selektivní serializace
Třída často obsahuje pole, která by neměla být serializována. Můžete například předpokládat, že třída uchovává ID vlákna v členské proměnné. Při deserializaci třídy vlákno uloženo ID pro, když byla třída serializována, již pravděpodobně není spuštěna; Proto serializace této hodnoty nemá smysl. Můžete zabránit serializaci členských proměnných jejich označením pomocí [Neserializovaného](xref:System.NonSerializedAttribute) atributu následujícím způsobem.  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

Přesvědčte se, pokud je to možné, objekt, který by mohl obsahovat nonserializable data citlivá na zabezpečení. Pokud objekt musí být serializován, použijte `NonSerialized` atribut pro konkrétní pole, která ukládají citlivá data. Pokud tato pole nevylučujete ze serializace, uvědomte si, že data, která jsou uložena, jsou vystavena jakémukoli kódu, který má oprávnění k serializaci. Další informace o psaní kódu zabezpečené serializace naleznete v tématu [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také

- [Binární serializace](binary-serialization.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
- [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)

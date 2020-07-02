---
ms.openlocfilehash: ae0f68a19d6eae53998d61e924cfef3aaaec1784
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619969"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>ConcurrentDictionary serializovaný v .NET Framework 4,5 s NetDataContractSerializer nelze deserializovat pomocí .NET Framework 4.5.1 nebo 4.5.2.

#### <a name="details"></a>Podrobnosti

Kvůli vnitřním změnám typu <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekty, které jsou serializovány s .NET Framework 4,5 pomocí, <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> Nelze deserializovat v .NET Framework 4.5.1 nebo v .NET Framework 4.5.2. Všimněte si, že přechází do druhého směru (serializace s .NET Framework 4.5. x a deserializace s .NET Framework 4,5) funguje. Podobně, všechny 4. x serializace mezi verzemi funguje s .NET Framework 4.6. serializace a deserializace s jednou verzí .NET Framework není ovlivněna.

#### <a name="suggestion"></a>Návrh

Pokud je nutné serializovat a deserializovat <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> mezi .NET Framework 4,5 a .NET Framework 4.5.1/4.5.2, je třeba použít alternativní serializátor, jako je například <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> serializátor nebo, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> namísto <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> . Další možností je, že tento problém je vyřešen v .NET Framework 4,6, lze jej vyřešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime|

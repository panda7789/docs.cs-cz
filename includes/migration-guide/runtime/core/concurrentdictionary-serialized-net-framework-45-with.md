---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858561"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>ConcurrentDictionary serializované v rozhraní .NET Framework 4.5 s NetDataContractSerializer nelze rekonstruovat pomocí rozhraní .NET Framework 4.5.1 nebo 4.5.2

|   |   |
|---|---|
|Podrobnosti|Z důvodu vnitřní změny <xref:System.Collections.Concurrent.ConcurrentDictionary%602> typu objekty, které jsou serializovány s <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> rozhraním .NET Framework 4.5 pomocí nelze rekonstruovat v rozhraní .NET Framework 4.5.1 nebo v rozhraní .NET Framework 4.5.2.Všimněte si, že pohybující se v opačném směru (serializace s rozhraním .NET Framework 4.5.x a deserializace s rozhraním .NET Framework 4.5) funguje. Podobně všechny serializace 4.x mezi verzemi pracuje s rozhraním .NET Framework 4.6.Serializace a deserializace s jedinou verzí rozhraní .NET Framework není ovlivněna.|
|Návrh|Pokud je nutné serializovat a rekonstruovat <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> mezi rozhraními .NET Framework 4.5 a .NET Framework 4.5.1/4.5.2, měl by být <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>místo serializátoru použit alternativní serializátor, jako <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> je serializátor nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializátor . Alternativně vzhledem k tomu, že tento problém je vyřešen v rozhraní .NET Framework 4.6, může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235306"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>ConcurrentDictionary serializován v rozhraní .NET Framework 4.5 s NetDataContractSerializer nemůže deserializovat rozhraním .NET Framework 4.5.1 a 4.5.2

|   |   |
|---|---|
|Podrobnosti|Z důvodu interní změny na typ <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekty serializované pomocí rozhraní .NET Framework 4.5 pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> nejde deserializovat v rozhraní .NET Framework 4.5.1 nebo v rozhraní .NET Framework 4.5.2.Note to přesunutí v jiných směr ( serializace s použitím rozhraní .NET Framework 4.5.x a deserializaci pomocí rozhraní .NET Framework 4.5) funguje. Podobně veškerou serializaci mezi různými verzemi 4.x funguje s 4.6.Serializing rozhraní .NET Framework a deserializaci v jedné verzi rozhraní .NET Framework nemá vliv.|
|Doporučení|Pokud je nutné k serializaci a deserializaci <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> mezi .NET Framework 4.5 a 4.5.1/4.5.2 rozhraní .NET Framework, jako jsou alternativní serializátor <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializátor by měla být použita místo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Alternativně vzhledem k tomu, že tento problém je vyřešen v rozhraní .NET Framework 4.6, ho může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Modul runtime|

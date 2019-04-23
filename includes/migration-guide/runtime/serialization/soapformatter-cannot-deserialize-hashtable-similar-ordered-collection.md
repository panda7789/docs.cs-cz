---
ms.openlocfilehash: 6ed7438a7f6e7710fcce03c8260a1360143f8d93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235259"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter nelze deserializovat zatřiďovací tabulky a podobné objekty kolekcí

|   |   |
|---|---|
|Podrobnosti|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Není zárukou, že se objekty serializují v rámci jedné verzi rozhraní .NET Framework se úspěšně deserializovat pod jinou verzi nepodporuje. Konkrétně některé seřazené kolekce (jako je <xref:System.Collections.Hashtable?displayProperty=name>) přidaly členy mezi 4.0 a 4.5 tak, aby tyto typy objektů nelze rekonstruovat pomocí rozhraní .NET Framework 4.0, pokud byly serializované pomocí rozhraní .NET Framework 4.5. Všimněte si, že pokud serializovaná data jak serializovat a deserializovat se stejnou verzí rozhraní .NET Framework, bez problému.|
|Doporučení|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> serializace by měla být nahrazena <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializace nebo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> chcete být odolní vůči změn rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

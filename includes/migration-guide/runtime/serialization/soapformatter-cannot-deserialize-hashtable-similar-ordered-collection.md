---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620059"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter nemůže deserializovat zatřiďovací tabulku a podobné objekty kolekce.

#### <a name="details"></a>Podrobnosti

<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>Nezaručuje, že objekty serializované v rámci jedné .NET Framework verze budou úspěšně deserializovány pod jinou verzí. Konkrétně některé seřazené kolekce (jako <xref:System.Collections.Hashtable?displayProperty=fullName> ) přidaly členy mezi 4,0 a 4,5, aby objekty těchto typů nebylo možné deserializovat pomocí .NET Framework 4,0, pokud byly serializovány pomocí .NET Framework 4,5. Všimněte si, že jsou-li Serializovaná data serializována i deserializována se stejnou .NET Framework verzí, nebude provedena žádná chyba.

#### <a name="suggestion"></a>Návrh

<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>serializace by měla být nahrazena <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializací nebo může <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> být odolná proti .NET Framework změnám.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

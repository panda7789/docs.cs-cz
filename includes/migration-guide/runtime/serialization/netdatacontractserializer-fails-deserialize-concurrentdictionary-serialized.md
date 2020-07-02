---
ms.openlocfilehash: eef5633ec8566f6d5216b7dca4387766cacb600d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620062"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer nemůže deserializovat ConcurrentDictionary serializovaný pomocí jiné verze rozhraní .NET.

#### <a name="details"></a>Podrobnosti

Podle návrhu <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> lze použít pouze v případě, že serializace a deserializace ukončí sdílení stejných typů CLR. Proto není zaručeno, že objekt serializovaný pomocí jedné verze .NET Framework lze deserializovat jinou verzí.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> je typ, který se označuje jako neserializace správně v případě, že je serializovaná s .NET Framework 4,5 nebo starším a deserializována s .NET Framework 4.5.1 nebo novějším.

#### <a name="suggestion"></a>Návrh

K dispozici je několik možných meziproblémových řešení tohoto problému:<ul><li>Upgradujte počítač serializace na použití .NET Framework 4.5.1 i.</li><li><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>Místo toho použijte <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> , protože neočekává přesně stejné typy CLR jak v serializaci, tak i deserializaci na konci.</li><li><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>Místo toho použijte, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> protože neprojeví tuto konkrétní přerušení 4,5- &gt; 4.5.1.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

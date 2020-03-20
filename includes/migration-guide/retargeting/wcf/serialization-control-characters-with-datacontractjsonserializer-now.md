---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77465967"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializace řídicích znaků pomocí datacontractjsonserializer je nyní kompatibilní s ECMAScript V6 a V8

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> a starších verzích nebyly některé speciální řídicí znaky, například \b, \f a \t, serializovat způsobem, který byl kompatibilní se standardy ECMAScript V6 a V8. Počínaje rozhraním .NET Framework 4.7 je serializace těchto řídicích znaků kompatibilní s ecmascriptovými v6 a v8.|
|Návrh|Pro aplikace, které cílí na rozhraní .NET Framework 4.7, je tato funkce ve výchozím nastavení povolena. Pokud toto chování není žádoucí, můžete se odhlásit z <code>&lt;runtime&gt;</code> této funkce přidáním následujícího řádku do části souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

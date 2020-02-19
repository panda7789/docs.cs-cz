---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465967"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializace řídicích znaků pomocí DataContractJsonSerializer je teď kompatibilní s ECMAScript V6 a V8

|   |   |
|---|---|
|Podrobnosti|V .NET Framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> nebyly serializovány některé speciální řídicí znaky, například \b, \f a \t, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8. Počínaje .NET Framework 4,7 je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.|
|Návrh|U aplikací, které cílí na .NET Framework 4,7, je tato funkce ve výchozím nastavení povolená. Není-li toto chování žádoucí, můžete se odhlásit z této funkce přidáním následujícího řádku do oddílu <code>&lt;runtime&gt;</code> souboru App. config nebo Web. config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Verze|4.7|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

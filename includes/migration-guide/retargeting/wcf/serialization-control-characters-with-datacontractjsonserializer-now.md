---
ms.openlocfilehash: 2f5511b7694f91893b731805119b85d1a5669a33
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859111"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializace řídicí znaky s DataContractJsonSerializer je teď kompatibilní se ECMAScript V6 a v8:

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET framework 4.6.2 a předchozími verzemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> nelze serializovat některé speciální řídicí znaky, jako je například \b \f a \t tak, aby byla kompatibilní se standardy ECMAScript V6 a V8. Od verze rozhraní .NET Framework 4.7, je kompatibilní s ECMAScript V6 a V8 serializace tyto řídicí znaky.|
|Doporučení|Pro aplikace, které cílí .NET Framework 4.7 Tato funkce povolena ve výchozím nastavení. Pokud toto chování není žádoucí, můžete se rozhodnout tuto funkci tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|


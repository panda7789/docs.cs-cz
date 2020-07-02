---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614531"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializace řídicích znaků pomocí DataContractJsonSerializer je teď kompatibilní s ECMAScript V6 a V8

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 a dřívějších verzích nedošlo k <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> serializaci některých speciálních řídicích znaků, například \b, \f a \t, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8. Počínaje .NET Framework 4,7 je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.

#### <a name="suggestion"></a>Návrh

U aplikací, které cílí na .NET Framework 4,7, je tato funkce ve výchozím nastavení povolená. Není-li toto chování žádoucí, můžete tuto funkci odhlásit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>

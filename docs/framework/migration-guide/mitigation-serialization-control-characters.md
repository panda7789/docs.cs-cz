---
title: Serializace řídicích znaků pomocí datacontractjsonserializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181202"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Zmírnění: Serializace řídicích znaků pomocí dataContractJsonSerializer

Počínaje rozhraním .NET Framework 4.7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se změnil způsob serializace řídicích znaků podle rozhraní ECMAScript V6 a V8.

## <a name="impact"></a>Dopad

V rozhraní .NET Framework 4.6.2 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a starších verzích nebyly serializovat `\b` `\f`některé `\t`speciální řídicí znaky, například , a , způsobem, který byl kompatibilní se standardy ECMAScript V6 a V8.

U aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7, je serializace těchto řídicích znaků kompatibilní s ecmascriptovými v6 a v8. Následující jsou ovlivněny:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Omezení rizik

U aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7, je toto chování ve výchozím nastavení povoleno.

Pokud toto chování není žádoucí, můžete se odhlásit z `<runtime>` této funkce přidáním následujícího řádku do části souboru app.config nebo web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)

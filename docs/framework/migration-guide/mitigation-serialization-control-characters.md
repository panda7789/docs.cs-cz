---
title: Serializace řídicích znaků pomocí DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346575"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer

Počínaje .NET Framework 4,7 se způsob, jakým jsou řídicí znaky serializovány pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změněna tak, aby odpovídaly ECMAScript V6 a V8. 
 
## <a name="impact"></a>Dopad

V rozhraní .NET Framework 4.6.2 a starších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> neserializovat některé speciální řídicí znaky, například `\b`, `\f`a `\t`, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.

Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8. Ovlivněna jsou následující rozhraní API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Zmírnění

U aplikací, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.

Není-li toto chování žádoucí, můžete se odhlásit z této funkce přidáním následujícího řádku do oddílu `<runtime>` souboru App. config nebo Web. config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)

---
title: 'Zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: faa7a32766a3ea1ef9cddcdb8af8fd0dd5a6f287
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457803"
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

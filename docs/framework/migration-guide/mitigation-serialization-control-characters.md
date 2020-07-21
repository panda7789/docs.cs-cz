---
title: Serializace řídicích znaků pomocí DataContractJsonSerializer
description: Přečtěte si o tom, jak se serializace řídicích znaků změnila tak, aby odpovídala ECMAScript V6 a V8 v .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475382"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer

Počínaje .NET Framework 4,7, způsob, jakým jsou řídicí znaky serializovány pomocí, se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změnila tak, aby odpovídala ECMAScript V6 a V8.

## <a name="impact"></a>Dopad

V .NET Framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nedošlo k serializaci některých speciálních řídicích znaků, jako například `\b` , `\f` a `\t` , způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.

Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8. Ovlivněna jsou následující rozhraní API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Omezení rizik

Pro aplikace, které cílí na verze .NET Framework od .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.

Není-li toto chování žádoucí, můžete tuto funkci odhlásit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)

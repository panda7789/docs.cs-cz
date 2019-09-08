---
title: Zmírnění Serializace řídicích znaků pomocí DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789840"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Zmírnění Serializace řídicích znaků pomocí DataContractJsonSerializer

Počínaje .NET Framework 4,7, způsob, jakým jsou řídicí znaky serializovány pomocí, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se změnila tak, aby odpovídala ECMAScript V6 a V8. 
 
## <a name="impact"></a>Dopad

V rozhraní .NET Framework 4.6.2 a starších verzích nedošlo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci některých speciálních řídicích znaků, `\b`například, `\f`a `\t`, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.

Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8. Ovlivněna jsou následující rozhraní API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Zmírnění

U aplikací, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.

Není-li toto chování žádoucí, můžete se odhlásit z této funkce přidáním následujícího řádku do `<runtime>` oddílu souboru App. config nebo Web. config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Viz také:

- [Změna cílení změn v .NET Framework 4,7](retargeting-changes-in-the-net-framework-4-7.md)

---
title: 'Omezení rizik: Serializace s objektu DataContractJsonSerializer. řídicí znaky'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a00edbf2d5833349de14986f2a57a2c943f3ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388430"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Omezení rizik: Serializace s objektu DataContractJsonSerializer. řídicí znaky

Od verze 4.7 rozhraní .NET Framework, způsob, ve které řízení znaky jsou serializovat s příznakem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> došlo ke změně tak, aby odpovídala ECMAScript V6 a v8:. 
 
## <a name="impact"></a>Dopad

V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> není serializovat například některé speciální řídicí znaky `\b`, `\f`, a `\t`, tak, aby byla kompatibilní se standardy ECMAScript V6 a v8:.

Pro aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7 rozhraní .NET Framework je kompatibilní s ECMAScript V6 a v8: serializace tyto řídicí znaky. Následující rozhraní API se vztahuje:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Zmírnění

Pro aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7 rozhraní .NET Framework toto chování je standardně povolená.

Pokud toto chování není žádoucí, můžete zamítnutí této funkce přidáním následující řádek do `<runtime>` v souboru app.config nebo web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Viz také
[Změny cílení v rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

---
title: 'Omezení rizik: Serializace ovládacího prvku znaků s vlastností objektu DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31f946fa01f3d6334011098d12483445159ce54a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738115"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Omezení rizik: Serializace ovládacího prvku znaků s vlastností objektu DataContractJsonSerializer

Od verze rozhraní .NET Framework 4.7, způsob, ve které ovládací prvek znaky jsou serializovat s příznakem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změnila tak, aby odpovídal ECMAScript V6 a V8. 
 
## <a name="impact"></a>Dopad

V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> není serializovat jako některé speciální řídicí znaky `\b`, `\f`, a `\t`, tak, aby byla kompatibilní se standardy ECMAScript V6 a V8.

U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 je kompatibilní s ECMAScript V6 a V8 serializace tyto řídicí znaky. Jsou ovlivněny následující rozhraní API:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Zmírnění

U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 pro toto chování je standardně povolená.

Pokud toto chování není žádoucí, můžete se rozhodnout tuto funkci tak, že přidáte následující řádek, který `<runtime>` část souboru app.config nebo web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Viz také:
- [Změny cílení v rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

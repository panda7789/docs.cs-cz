---
title: "Omezení rizik: Serializace s objektu DataContractJsonSerializer. řídicí znaky"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e92bc1ab55674a39331cef5d0450cd8e28ef55f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="e95b9-102">Omezení rizik: Serializace s objektu DataContractJsonSerializer. řídicí znaky</span><span class="sxs-lookup"><span data-stu-id="e95b9-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="e95b9-103">Od verze 4.7 rozhraní .NET Framework, způsob, ve které řízení znaky jsou serializovat s příznakem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> došlo ke změně tak, aby odpovídala ECMAScript V6 a v8:.</span><span class="sxs-lookup"><span data-stu-id="e95b9-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="e95b9-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="e95b9-104">Impact</span></span>

<span data-ttu-id="e95b9-105">V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> není serializovat například některé speciální řídicí znaky `\b`, `\f`, a `\t`, tak, aby byla kompatibilní se standardy ECMAScript V6 a v8:.</span><span class="sxs-lookup"><span data-stu-id="e95b9-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="e95b9-106">Pro aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7 rozhraní .NET Framework je kompatibilní s ECMAScript V6 a v8: serializace tyto řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="e95b9-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="e95b9-107">Následující rozhraní API se vztahuje:</span><span class="sxs-lookup"><span data-stu-id="e95b9-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="e95b9-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="e95b9-108">Mitigation</span></span>

<span data-ttu-id="e95b9-109">Pro aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7 rozhraní .NET Framework toto chování je standardně povolená.</span><span class="sxs-lookup"><span data-stu-id="e95b9-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="e95b9-110">Pokud toto chování není žádoucí, můžete zamítnutí této funkce přidáním následující řádek do `<runtime>` v souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="e95b9-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="e95b9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e95b9-111">See also</span></span>
[<span data-ttu-id="e95b9-112">Změny cílení v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e95b9-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

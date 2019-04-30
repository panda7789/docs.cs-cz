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
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871368"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="ef630-102">Omezení rizik: Serializace ovládacího prvku znaků s vlastností objektu DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ef630-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="ef630-103">Od verze rozhraní .NET Framework 4.7, způsob, ve které ovládací prvek znaky jsou serializovat s příznakem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změnila tak, aby odpovídal ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="ef630-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="ef630-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="ef630-104">Impact</span></span>

<span data-ttu-id="ef630-105">V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> není serializovat jako některé speciální řídicí znaky `\b`, `\f`, a `\t`, tak, aby byla kompatibilní se standardy ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="ef630-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="ef630-106">U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 je kompatibilní s ECMAScript V6 a V8 serializace tyto řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="ef630-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="ef630-107">Jsou ovlivněny následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="ef630-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="ef630-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="ef630-108">Mitigation</span></span>

<span data-ttu-id="ef630-109">U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 pro toto chování je standardně povolená.</span><span class="sxs-lookup"><span data-stu-id="ef630-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="ef630-110">Pokud toto chování není žádoucí, můžete se rozhodnout tuto funkci tak, že přidáte následující řádek, který `<runtime>` část souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="ef630-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="ef630-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef630-111">See also</span></span>

- [<span data-ttu-id="ef630-112">Změny cílení v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ef630-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

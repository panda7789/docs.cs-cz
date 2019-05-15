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
ms.openlocfilehash: e7e316f874a2b559cb3fe9d64a9ec7cf25addbe5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557764"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="a7eab-102">Omezení rizik: Serializace ovládacího prvku znaků s vlastností objektu DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="a7eab-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="a7eab-103">Od verze rozhraní .NET Framework 4.7, způsob, ve které ovládací prvek znaky jsou serializovat s příznakem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změnila tak, aby odpovídal ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="a7eab-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="a7eab-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="a7eab-104">Impact</span></span>

<span data-ttu-id="a7eab-105">V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> není serializovat jako některé speciální řídicí znaky `\b`, `\f`, a `\t`, tak, aby byla kompatibilní se standardy ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="a7eab-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="a7eab-106">U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 je kompatibilní s ECMAScript V6 a V8 serializace tyto řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="a7eab-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="a7eab-107">Jsou ovlivněny následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a7eab-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="a7eab-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="a7eab-108">Mitigation</span></span>

<span data-ttu-id="a7eab-109">U aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.7 pro toto chování je standardně povolená.</span><span class="sxs-lookup"><span data-stu-id="a7eab-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="a7eab-110">Pokud toto chování není žádoucí, můžete se rozhodnout tuto funkci tak, že přidáte následující řádek, který `<runtime>` část souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="a7eab-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="a7eab-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7eab-111">See also</span></span>

- [<span data-ttu-id="a7eab-112">Změny cílení v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="a7eab-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

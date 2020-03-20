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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="36b1d-102">Zmírnění: Serializace řídicích znaků pomocí dataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="36b1d-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="36b1d-103">Počínaje rozhraním .NET Framework 4.7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se změnil způsob serializace řídicích znaků podle rozhraní ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="36b1d-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="36b1d-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="36b1d-104">Impact</span></span>

<span data-ttu-id="36b1d-105">V rozhraní .NET Framework 4.6.2 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a starších verzích nebyly serializovat `\b` `\f`některé `\t`speciální řídicí znaky, například , a , způsobem, který byl kompatibilní se standardy ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="36b1d-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="36b1d-106">U aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7, je serializace těchto řídicích znaků kompatibilní s ecmascriptovými v6 a v8.</span><span class="sxs-lookup"><span data-stu-id="36b1d-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="36b1d-107">Následující jsou ovlivněny:</span><span class="sxs-lookup"><span data-stu-id="36b1d-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="36b1d-108">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="36b1d-108">Mitigation</span></span>

<span data-ttu-id="36b1d-109">U aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7, je toto chování ve výchozím nastavení povoleno.</span><span class="sxs-lookup"><span data-stu-id="36b1d-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="36b1d-110">Pokud toto chování není žádoucí, můžete se odhlásit z `<runtime>` této funkce přidáním následujícího řádku do části souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="36b1d-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="36b1d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="36b1d-111">See also</span></span>

- [<span data-ttu-id="36b1d-112">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="36b1d-112">Application compatibility</span></span>](application-compatibility.md)

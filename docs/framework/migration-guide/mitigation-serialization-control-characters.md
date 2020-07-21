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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="c1e2d-103">Zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="c1e2d-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="c1e2d-104">Počínaje .NET Framework 4,7, způsob, jakým jsou řídicí znaky serializovány pomocí, se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změnila tak, aby odpovídala ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="c1e2d-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="c1e2d-105">Impact</span></span>

<span data-ttu-id="c1e2d-106">V .NET Framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nedošlo k serializaci některých speciálních řídicích znaků, jako například `\b` , `\f` a `\t` , způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="c1e2d-107">Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="c1e2d-108">Ovlivněna jsou následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="c1e2d-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="c1e2d-109">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="c1e2d-109">Mitigation</span></span>

<span data-ttu-id="c1e2d-110">Pro aplikace, které cílí na verze .NET Framework od .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="c1e2d-111">Není-li toto chování žádoucí, můžete tuto funkci odhlásit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:</span><span class="sxs-lookup"><span data-stu-id="c1e2d-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="c1e2d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1e2d-112">See also</span></span>

- [<span data-ttu-id="c1e2d-113">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="c1e2d-113">Application compatibility</span></span>](application-compatibility.md)

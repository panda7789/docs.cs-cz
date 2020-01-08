---
title: Serializace řídicích znaků pomocí DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346575"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="e0be4-102">Zmírnění rizika: serializace řídicích znaků pomocí DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="e0be4-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="e0be4-103">Počínaje .NET Framework 4,7 se způsob, jakým jsou řídicí znaky serializovány pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> změněna tak, aby odpovídaly ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="e0be4-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="e0be4-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="e0be4-104">Impact</span></span>

<span data-ttu-id="e0be4-105">V rozhraní .NET Framework 4.6.2 a starších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> neserializovat některé speciální řídicí znaky, například `\b`, `\f`a `\t`, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="e0be4-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="e0be4-106">Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="e0be4-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="e0be4-107">Ovlivněna jsou následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="e0be4-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="e0be4-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="e0be4-108">Mitigation</span></span>

<span data-ttu-id="e0be4-109">U aplikací, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="e0be4-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="e0be4-110">Není-li toto chování žádoucí, můžete se odhlásit z této funkce přidáním následujícího řádku do oddílu `<runtime>` souboru App. config nebo Web. config:</span><span class="sxs-lookup"><span data-stu-id="e0be4-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="e0be4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0be4-111">See also</span></span>

- [<span data-ttu-id="e0be4-112">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e0be4-112">Application compatibility</span></span>](application-compatibility.md)

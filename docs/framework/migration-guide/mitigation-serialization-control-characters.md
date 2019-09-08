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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="9ceb7-102">Zmírnění Serializace řídicích znaků pomocí DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="9ceb7-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="9ceb7-103">Počínaje .NET Framework 4,7, způsob, jakým jsou řídicí znaky serializovány pomocí, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se změnila tak, aby odpovídala ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="9ceb7-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="9ceb7-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="9ceb7-104">Impact</span></span>

<span data-ttu-id="9ceb7-105">V rozhraní .NET Framework 4.6.2 a starších verzích nedošlo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci některých speciálních řídicích znaků, `\b`například, `\f`a `\t`, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="9ceb7-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="9ceb7-106">Pro aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="9ceb7-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="9ceb7-107">Ovlivněna jsou následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="9ceb7-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="9ceb7-108">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="9ceb7-108">Mitigation</span></span>

<span data-ttu-id="9ceb7-109">U aplikací, které cílí na verze .NET Framework počínaje .NET Framework 4,7, je toto chování ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="9ceb7-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="9ceb7-110">Není-li toto chování žádoucí, můžete se odhlásit z této funkce přidáním následujícího řádku do `<runtime>` oddílu souboru App. config nebo Web. config:</span><span class="sxs-lookup"><span data-stu-id="9ceb7-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="9ceb7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ceb7-111">See also</span></span>

- [<span data-ttu-id="9ceb7-112">Změna cílení změn v .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="9ceb7-112">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)

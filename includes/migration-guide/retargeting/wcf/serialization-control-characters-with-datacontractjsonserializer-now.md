---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614531"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="b5f05-101">Serializace řídicích znaků pomocí DataContractJsonSerializer je teď kompatibilní s ECMAScript V6 a V8</span><span class="sxs-lookup"><span data-stu-id="b5f05-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="b5f05-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5f05-102">Details</span></span>

<span data-ttu-id="b5f05-103">V .NET Framework 4.6.2 a dřívějších verzích nedošlo k <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> serializaci některých speciálních řídicích znaků, například \b, \f a \t, způsobem, který byl kompatibilní s normami ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="b5f05-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="b5f05-104">Počínaje .NET Framework 4,7 je serializace těchto řídicích znaků kompatibilní s ECMAScript V6 a V8.</span><span class="sxs-lookup"><span data-stu-id="b5f05-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b5f05-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="b5f05-105">Suggestion</span></span>

<span data-ttu-id="b5f05-106">U aplikací, které cílí na .NET Framework 4,7, je tato funkce ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="b5f05-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="b5f05-107">Není-li toto chování žádoucí, můžete tuto funkci odhlásit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:</span><span class="sxs-lookup"><span data-stu-id="b5f05-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="b5f05-108">Name</span><span class="sxs-lookup"><span data-stu-id="b5f05-108">Name</span></span>    | <span data-ttu-id="b5f05-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b5f05-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b5f05-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b5f05-110">Scope</span></span>   | <span data-ttu-id="b5f05-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b5f05-111">Edge</span></span>        |
| <span data-ttu-id="b5f05-112">Verze</span><span class="sxs-lookup"><span data-stu-id="b5f05-112">Version</span></span> | <span data-ttu-id="b5f05-113">4,7</span><span class="sxs-lookup"><span data-stu-id="b5f05-113">4.7</span></span>         |
| <span data-ttu-id="b5f05-114">Typ</span><span class="sxs-lookup"><span data-stu-id="b5f05-114">Type</span></span>    | <span data-ttu-id="b5f05-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b5f05-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b5f05-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5f05-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>

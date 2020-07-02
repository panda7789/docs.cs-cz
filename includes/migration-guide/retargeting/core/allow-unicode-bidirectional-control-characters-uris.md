---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614428"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="3cc8c-101">Povoluje v identifikátorech URI obousměrné řídicí znaky (Unicode).</span><span class="sxs-lookup"><span data-stu-id="3cc8c-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="3cc8c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3cc8c-102">Details</span></span>

<span data-ttu-id="3cc8c-103">Unicode určuje několik speciálních řídicích znaků, které se používají k určení orientace textu.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="3cc8c-104">V předchozích verzích .NET Framework byly tyto znaky nesprávně odstraněny ze všech identifikátorů URI i v případě, že byly přítomny ve formuláři s kódováním v procentech.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="3cc8c-105">Aby bylo možné lépe dodržovat [specifikaci RFC 3987](https://tools.ietf.org/html/rfc3987), teď tyto znaky povolujeme v identifikátorech URI.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="3cc8c-106">Pokud se v identifikátoru URI najde nekódovaný, jsou v procentech zakódované.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="3cc8c-107">V případě, že nalezené procento jsou zakódovány, jsou ponechány, jak jsou.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3cc8c-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="3cc8c-108">Suggestion</span></span>

<span data-ttu-id="3cc8c-109">Pro aplikace, které cílí na verze .NET Framework počínaje 4.7.2, je ve výchozím nastavení povolená podpora obousměrných znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="3cc8c-110">Pokud je tato změna nežádoucí, můžete ji zakázat přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="3cc8c-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="3cc8c-111">Pro aplikace, které cílí na starší verze .NET Framework, ale běží v rámci verzí počínaje .NET Framework 4.7.2, je ve výchozím nastavení zakázaná podpora obousměrných znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3cc8c-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="3cc8c-112">Můžete ji povolit přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace::</span><span class="sxs-lookup"><span data-stu-id="3cc8c-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="3cc8c-113">Name</span><span class="sxs-lookup"><span data-stu-id="3cc8c-113">Name</span></span>    | <span data-ttu-id="3cc8c-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3cc8c-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3cc8c-115">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3cc8c-115">Scope</span></span>   | <span data-ttu-id="3cc8c-116">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="3cc8c-116">Minor</span></span>       |
| <span data-ttu-id="3cc8c-117">Verze</span><span class="sxs-lookup"><span data-stu-id="3cc8c-117">Version</span></span> | <span data-ttu-id="3cc8c-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3cc8c-118">4.7.2</span></span>       |
| <span data-ttu-id="3cc8c-119">Typ</span><span class="sxs-lookup"><span data-stu-id="3cc8c-119">Type</span></span>    | <span data-ttu-id="3cc8c-120">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="3cc8c-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3cc8c-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3cc8c-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

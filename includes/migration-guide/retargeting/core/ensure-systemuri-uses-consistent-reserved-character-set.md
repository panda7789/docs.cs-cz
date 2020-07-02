---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614445"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="491c8-101">Zajistěte, aby System. URI používal konzistentní vyhrazenou znakovou sadu.</span><span class="sxs-lookup"><span data-stu-id="491c8-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="491c8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="491c8-102">Details</span></span>

<span data-ttu-id="491c8-103">V <xref:System.Uri?displayProperty=fullName> je teď zakódovaných znaků, které jsou v procentech zakódovaných v procentech, trvale zakódované.</span><span class="sxs-lookup"><span data-stu-id="491c8-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="491c8-104">K tomu dojde v rámci vlastností a metod, které přistupují k komponentám URI, dotaz, fragment nebo UserInfo.</span><span class="sxs-lookup"><span data-stu-id="491c8-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="491c8-105">Chování se změní jenom v případě, že jsou splněné obě následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="491c8-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="491c8-106">Identifikátor URI obsahuje kódovaný tvar libovolného z následujících vyhrazených znaků: `:` , `'` , `(` , `)` `!` nebo `*` .</span><span class="sxs-lookup"><span data-stu-id="491c8-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="491c8-107">Identifikátor URI obsahuje znak Unicode nebo kódovaný nevyhrazený znak.</span><span class="sxs-lookup"><span data-stu-id="491c8-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="491c8-108">Pokud jsou obě výše uvedené pravdivé, zakódované vyhrazené znaky jsou zakódované vlevo.</span><span class="sxs-lookup"><span data-stu-id="491c8-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="491c8-109">V předchozích verzích .NET Framework jsou Dekódovatelné.</span><span class="sxs-lookup"><span data-stu-id="491c8-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="491c8-110">Návrh</span><span class="sxs-lookup"><span data-stu-id="491c8-110">Suggestion</span></span>

<span data-ttu-id="491c8-111">U aplikací, které cílí na verze .NET Framework počínaje 4.7.2, je ve výchozím nastavení povolené nové chování při dekódování.</span><span class="sxs-lookup"><span data-stu-id="491c8-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="491c8-112">Pokud je tato změna nežádoucí, můžete ji zakázat přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="491c8-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="491c8-113">U aplikací, které cílí na starší verze .NET Framework, ale běží v rámci verzí počínaje .NET Framework 4.7.2, je ve výchozím nastavení zakázané nové chování při dekódování.</span><span class="sxs-lookup"><span data-stu-id="491c8-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="491c8-114">Můžete ji povolit přidáním následujícího přepínače [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="491c8-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="491c8-115">Name</span><span class="sxs-lookup"><span data-stu-id="491c8-115">Name</span></span>    | <span data-ttu-id="491c8-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="491c8-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="491c8-117">Rozsah</span><span class="sxs-lookup"><span data-stu-id="491c8-117">Scope</span></span>   | <span data-ttu-id="491c8-118">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="491c8-118">Minor</span></span>       |
| <span data-ttu-id="491c8-119">Verze</span><span class="sxs-lookup"><span data-stu-id="491c8-119">Version</span></span> | <span data-ttu-id="491c8-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="491c8-120">4.7.2</span></span>       |
| <span data-ttu-id="491c8-121">Typ</span><span class="sxs-lookup"><span data-stu-id="491c8-121">Type</span></span>    | <span data-ttu-id="491c8-122">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="491c8-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="491c8-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="491c8-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

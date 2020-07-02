---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614580"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="0649b-101">Metoda PrivateFontCollection. AddFontFile uvolní prostředky písma.</span><span class="sxs-lookup"><span data-stu-id="0649b-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="0649b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0649b-102">Details</span></span>

<span data-ttu-id="0649b-103">V .NET Framework 4.7.1 a předchozích verzích <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> Třída neuvolní prostředky písma GDI+ po <xref:System.Drawing.Text.PrivateFontCollection> uvolnění pro <xref:System.Drawing.Font> objekty, které jsou přidány do této kolekce pomocí <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> metody.</span><span class="sxs-lookup"><span data-stu-id="0649b-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="0649b-104">Ve .NET Framework 4.7.2 a novější <xref:System.Drawing.Text.FontCollection.Dispose%2A> verze vydává písma GDI+, která byla přidána do kolekce jako soubory.</span><span class="sxs-lookup"><span data-stu-id="0649b-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0649b-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="0649b-105">Suggestion</span></span>

<span data-ttu-id="0649b-106">**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="0649b-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="0649b-107">Aplikace může tyto změny využít v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="0649b-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="0649b-108">Zkompiluje se znovu a zacílí na .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="0649b-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="0649b-109">Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="0649b-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="0649b-110">Cílí na .NET Framework 4.7.1 nebo dřívější verzi a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu app.config souboru a jeho nastavením na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0649b-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="0649b-111">Aplikace, které cílí na .NET Framework 4.7.2 nebo novější a chtějí zachovat starší verze chování, se můžou rozhodnout, že neuvolní prostředky písma explicitním nastavením tohoto přepínače AppContext na `true` .</span><span class="sxs-lookup"><span data-stu-id="0649b-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="0649b-112">Name</span><span class="sxs-lookup"><span data-stu-id="0649b-112">Name</span></span>    | <span data-ttu-id="0649b-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0649b-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0649b-114">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0649b-114">Scope</span></span>   | <span data-ttu-id="0649b-115">Edge</span><span class="sxs-lookup"><span data-stu-id="0649b-115">Edge</span></span>        |
| <span data-ttu-id="0649b-116">Verze</span><span class="sxs-lookup"><span data-stu-id="0649b-116">Version</span></span> | <span data-ttu-id="0649b-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="0649b-117">4.7.2</span></span>       |
| <span data-ttu-id="0649b-118">Typ</span><span class="sxs-lookup"><span data-stu-id="0649b-118">Type</span></span>    | <span data-ttu-id="0649b-119">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0649b-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0649b-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0649b-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>

---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614604"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="b94ce-101">Fokus klávesnice se teď přesouvá správně napříč několika vrstvami hostování WinForms nebo WPF.</span><span class="sxs-lookup"><span data-stu-id="b94ce-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="b94ce-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b94ce-102">Details</span></span>

<span data-ttu-id="b94ce-103">Zvažte použití aplikace WPF hostující ovládací prvek WinForms, který zase hostuje ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="b94ce-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="b94ce-104">Pokud je jako první nebo poslední ovládací prvek v této vrstvě WPF, uživatelé nemusí být schopni kartu vymezit z vrstvy WinForms `System.Windows.Forms.Integration.ElementHost` .</span><span class="sxs-lookup"><span data-stu-id="b94ce-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="b94ce-105">Tato změna opravuje tento problém a uživatelé teď mohou z vrstvy WinForms karet vymezit. Automatizované aplikace, které spoléhají na fokus bez použití uvozovacích znaků vrstvy WinForms, nemusí nadále fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="b94ce-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b94ce-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="b94ce-106">Suggestion</span></span>

<span data-ttu-id="b94ce-107">Vývojář, který chce tuto změnu využít při cílení na verzi architektury pod platformou .NET 4.7.2, může nastavit následující sadu příznaků AppContext na hodnotu false, aby bylo možné změnu povolit.</span><span class="sxs-lookup"><span data-stu-id="b94ce-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="b94ce-108">Aplikace WPF musí pro pozdější vylepšení získat výslovný souhlas se všemi vylepšeními přístupnosti v rané fázi.</span><span class="sxs-lookup"><span data-stu-id="b94ce-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="b94ce-109">Jinými slovy, `Switch.UseLegacyAccessibilityFeatures` a `Switch.UseLegacyAccessibilityFeatures.2` přepínači musí být setA vývojář, který vyžaduje předchozí funkčnost při cílení na rozhraní .NET 4.7.2 nebo vyšší, může nastavit následující příznak AppContext na hodnotu true, aby se změna zakázala.</span><span class="sxs-lookup"><span data-stu-id="b94ce-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b94ce-110">Name</span><span class="sxs-lookup"><span data-stu-id="b94ce-110">Name</span></span>    | <span data-ttu-id="b94ce-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b94ce-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b94ce-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b94ce-112">Scope</span></span>   | <span data-ttu-id="b94ce-113">Edge</span><span class="sxs-lookup"><span data-stu-id="b94ce-113">Edge</span></span>        |
| <span data-ttu-id="b94ce-114">Verze</span><span class="sxs-lookup"><span data-stu-id="b94ce-114">Version</span></span> | <span data-ttu-id="b94ce-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b94ce-115">4.7.2</span></span>       |
| <span data-ttu-id="b94ce-116">Typ</span><span class="sxs-lookup"><span data-stu-id="b94ce-116">Type</span></span>    | <span data-ttu-id="b94ce-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b94ce-117">Retargeting</span></span> |

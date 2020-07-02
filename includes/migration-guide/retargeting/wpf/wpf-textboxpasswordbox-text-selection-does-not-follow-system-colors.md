---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614621"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="0908b-101">Výběr textu v grafickém rozhraní WPF/PasswordBox nedodržuje systémové barvy</span><span class="sxs-lookup"><span data-stu-id="0908b-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="0908b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0908b-102">Details</span></span>

<span data-ttu-id="0908b-103">V .NET Framework 4.7.1 a dřívějších verzích, WPF `System.Windows.Controls.TextBox` a `System.Windows.Controls.PasswordBox` mohl by vykreslovat pouze výběr textu ve vrstvě doplňků.</span><span class="sxs-lookup"><span data-stu-id="0908b-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="0908b-104">V některých systémových motivech by to occlude text, takže je obtížné ho přečíst.</span><span class="sxs-lookup"><span data-stu-id="0908b-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="0908b-105">V .NET Framework 4.7.2 a novějších mají vývojáři možnost Povolit schéma vykreslování výběru založeného na doplňku bez doplňků, které tento problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="0908b-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0908b-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="0908b-106">Suggestion</span></span>

<span data-ttu-id="0908b-107">Vývojář, který chce využít tuto změnu, musí odpovídajícím způsobem nastavit následující příznak AppContext.</span><span class="sxs-lookup"><span data-stu-id="0908b-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="0908b-108">Aby bylo možné využít tuto funkci, musí být nainstalovaná verze .NET Framework 4.7.2 nebo novější. Chcete-li povolit výběr, který není založen na doplňky, použijte následující příznak AppContext.</span><span class="sxs-lookup"><span data-stu-id="0908b-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="0908b-109">Name</span><span class="sxs-lookup"><span data-stu-id="0908b-109">Name</span></span>    | <span data-ttu-id="0908b-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0908b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0908b-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0908b-111">Scope</span></span>   | <span data-ttu-id="0908b-112">Edge</span><span class="sxs-lookup"><span data-stu-id="0908b-112">Edge</span></span>        |
| <span data-ttu-id="0908b-113">Verze</span><span class="sxs-lookup"><span data-stu-id="0908b-113">Version</span></span> | <span data-ttu-id="0908b-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="0908b-114">4.7.2</span></span>       |
| <span data-ttu-id="0908b-115">Typ</span><span class="sxs-lookup"><span data-stu-id="0908b-115">Type</span></span>    | <span data-ttu-id="0908b-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0908b-116">Retargeting</span></span> |

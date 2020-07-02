---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617234"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="258e4-101">Pole TextBox.Text ve WPF nemusí být synchronizováno s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="258e4-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="258e4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="258e4-102">Details</span></span>

<span data-ttu-id="258e4-103">Pokud byla vlastnost <xref:System.Windows.Controls.TextBox.Text> změněna během operace zápisu datové vazby, v některých případech odráží předchozí hodnotu vlastnosti s datovou vazbou.</span><span class="sxs-lookup"><span data-stu-id="258e4-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="258e4-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="258e4-104">Suggestion</span></span>

<span data-ttu-id="258e4-105">To by nemělo mít žádný negativní dopad.</span><span class="sxs-lookup"><span data-stu-id="258e4-105">This should have no negative impact.</span></span> <span data-ttu-id="258e4-106">Předchozí chování však můžete obnovit nastavením vlastnosti <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na `false`.</span><span class="sxs-lookup"><span data-stu-id="258e4-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="258e4-107">Name</span><span class="sxs-lookup"><span data-stu-id="258e4-107">Name</span></span>    | <span data-ttu-id="258e4-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="258e4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="258e4-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="258e4-109">Scope</span></span>   | <span data-ttu-id="258e4-110">Edge</span><span class="sxs-lookup"><span data-stu-id="258e4-110">Edge</span></span>        |
| <span data-ttu-id="258e4-111">Verze</span><span class="sxs-lookup"><span data-stu-id="258e4-111">Version</span></span> | <span data-ttu-id="258e4-112">4.5</span><span class="sxs-lookup"><span data-stu-id="258e4-112">4.5</span></span>         |
|<span data-ttu-id="258e4-113">Typ</span><span class="sxs-lookup"><span data-stu-id="258e4-113">Type</span></span>|<span data-ttu-id="258e4-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="258e4-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="258e4-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="258e4-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>

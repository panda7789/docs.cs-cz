---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088483"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="87a90-101">Pole TextBox.Text ve WPF nemusí být synchronizováno s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="87a90-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="87a90-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="87a90-102">Details</span></span>|<span data-ttu-id="87a90-103">Pokud byla vlastnost <xref:System.Windows.Controls.TextBox.Text> změněna během operace zápisu datové vazby, v některých případech odráží předchozí hodnotu vlastnosti s datovou vazbou.</span><span class="sxs-lookup"><span data-stu-id="87a90-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="87a90-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="87a90-104">Suggestion</span></span>|<span data-ttu-id="87a90-105">To by nemělo mít žádný negativní dopad.</span><span class="sxs-lookup"><span data-stu-id="87a90-105">This should have no negative impact.</span></span> <span data-ttu-id="87a90-106">Předchozí chování však můžete obnovit nastavením vlastnosti <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="87a90-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="87a90-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="87a90-107">Scope</span></span>|<span data-ttu-id="87a90-108">Edge</span><span class="sxs-lookup"><span data-stu-id="87a90-108">Edge</span></span>|
|<span data-ttu-id="87a90-109">Version</span><span class="sxs-lookup"><span data-stu-id="87a90-109">Version</span></span>|<span data-ttu-id="87a90-110">4.5</span><span class="sxs-lookup"><span data-stu-id="87a90-110">4.5</span></span>|
|<span data-ttu-id="87a90-111">Type</span><span class="sxs-lookup"><span data-stu-id="87a90-111">Type</span></span>|<span data-ttu-id="87a90-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="87a90-112">Retargeting</span></span>|
|<span data-ttu-id="87a90-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="87a90-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

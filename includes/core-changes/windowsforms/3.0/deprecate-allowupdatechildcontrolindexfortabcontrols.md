---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936990"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="e1d3e-101">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="e1d3e-102">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e1d3e-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e1d3e-103">Change description</span></span>

<span data-ttu-id="e1d3e-104">V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="e1d3e-105">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="e1d3e-106">V rozhraní .NET Core není `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1d3e-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e1d3e-107">Version introduced</span></span>

<span data-ttu-id="e1d3e-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e1d3e-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1d3e-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e1d3e-109">Recommended action</span></span>

<span data-ttu-id="e1d3e-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-110">Remove the switch.</span></span> <span data-ttu-id="e1d3e-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="e1d3e-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e1d3e-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e1d3e-112">Category</span></span>

<span data-ttu-id="e1d3e-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1d3e-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1d3e-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e1d3e-114">Affected APIs</span></span>

- <span data-ttu-id="e1d3e-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1d3e-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

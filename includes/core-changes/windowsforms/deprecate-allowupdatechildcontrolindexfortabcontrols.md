---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181738"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="59c15-101">Přepínač kompatibility. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="59c15-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="59c15-102">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="59c15-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59c15-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="59c15-103">Change description</span></span>

<span data-ttu-id="59c15-104">V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="59c15-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="59c15-105">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="59c15-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="59c15-106">V rozhraní .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="59c15-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59c15-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="59c15-107">Version introduced</span></span>

<span data-ttu-id="59c15-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="59c15-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59c15-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="59c15-109">Recommended action</span></span>

<span data-ttu-id="59c15-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="59c15-110">Remove the switch.</span></span> <span data-ttu-id="59c15-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="59c15-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="59c15-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="59c15-112">Category</span></span>

<span data-ttu-id="59c15-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59c15-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59c15-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="59c15-114">Affected APIs</span></span>

- <span data-ttu-id="59c15-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="59c15-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

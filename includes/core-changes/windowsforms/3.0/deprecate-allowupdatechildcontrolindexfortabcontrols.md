---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643996"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="d229b-101">Přepínač kompatibility. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="d229b-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="d229b-102">Přepínač kompatibility `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` je podporován v model Windows Forms na .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d229b-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d229b-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="d229b-103">Change description</span></span>

<span data-ttu-id="d229b-104">V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d229b-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="d229b-105">Přepínač kompatibility `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="d229b-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="d229b-106">V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` podporován.</span><span class="sxs-lookup"><span data-stu-id="d229b-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d229b-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d229b-107">Version introduced</span></span>

<span data-ttu-id="d229b-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d229b-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d229b-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d229b-109">Recommended action</span></span>

<span data-ttu-id="d229b-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="d229b-110">Remove the switch.</span></span> <span data-ttu-id="d229b-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="d229b-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d229b-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d229b-112">Category</span></span>

<span data-ttu-id="d229b-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d229b-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d229b-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d229b-114">Affected APIs</span></span>

- <span data-ttu-id="d229b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d229b-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

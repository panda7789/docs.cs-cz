---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936990"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="09719-101">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.</span><span class="sxs-lookup"><span data-stu-id="09719-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="09719-102">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován ve formulářích Windows v rozhraní .NET Framework 4.6 a novějších verzích, ale není podporován ve formulářích Windows počínaje rozhraním .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="09719-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="09719-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="09719-103">Change description</span></span>

<span data-ttu-id="09719-104">V rozhraní .NET Framework 4.6 a novějších verzích výběr karty přeřazuje její kolekci ovládacích prvku.</span><span class="sxs-lookup"><span data-stu-id="09719-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="09719-105">Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto změny pořadí, pokud je toto chování nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="09719-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="09719-106">V rozhraní .NET `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` Core není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="09719-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="09719-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="09719-107">Version introduced</span></span>

<span data-ttu-id="09719-108">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="09719-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09719-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="09719-109">Recommended action</span></span>

<span data-ttu-id="09719-110">Odstraňte spínač.</span><span class="sxs-lookup"><span data-stu-id="09719-110">Remove the switch.</span></span> <span data-ttu-id="09719-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="09719-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="09719-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="09719-112">Category</span></span>

<span data-ttu-id="09719-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09719-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09719-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="09719-114">Affected APIs</span></span>

- <span data-ttu-id="09719-115">Žádný</span><span class="sxs-lookup"><span data-stu-id="09719-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

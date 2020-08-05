---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556155"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="e9a8a-101">Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="e9a8a-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Přepínač kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v rozhraní .NET Core nebo .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e9a8a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e9a8a-103">Change description</span></span>

<span data-ttu-id="e9a8a-104">V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="e9a8a-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Přepínač kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="e9a8a-106">V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9a8a-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e9a8a-107">Version introduced</span></span>

<span data-ttu-id="e9a8a-108">3.0</span><span class="sxs-lookup"><span data-stu-id="e9a8a-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9a8a-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e9a8a-109">Recommended action</span></span>

<span data-ttu-id="e9a8a-110">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-110">Remove the switch.</span></span> <span data-ttu-id="e9a8a-111">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="e9a8a-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e9a8a-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e9a8a-112">Category</span></span>

<span data-ttu-id="e9a8a-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9a8a-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9a8a-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e9a8a-114">Affected APIs</span></span>

- <span data-ttu-id="e9a8a-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9a8a-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

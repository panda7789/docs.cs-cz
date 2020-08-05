---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556152"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="7fb2d-101">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="7fb2d-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`Přepínač kompatibility není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7fb2d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="7fb2d-103">Change description</span></span>

<span data-ttu-id="7fb2d-104">V .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="7fb2d-105">V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-105">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7fb2d-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7fb2d-106">Version introduced</span></span>

<span data-ttu-id="7fb2d-107">3.0</span><span class="sxs-lookup"><span data-stu-id="7fb2d-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7fb2d-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7fb2d-108">Recommended action</span></span>

<span data-ttu-id="7fb2d-109">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-109">Remove the switch.</span></span> <span data-ttu-id="7fb2d-110">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="7fb2d-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="7fb2d-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7fb2d-111">Category</span></span>

<span data-ttu-id="7fb2d-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7fb2d-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7fb2d-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7fb2d-113">Affected APIs</span></span>

- <span data-ttu-id="7fb2d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="7fb2d-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

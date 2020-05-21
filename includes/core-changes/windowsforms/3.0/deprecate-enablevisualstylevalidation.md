---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721334"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="b48e9-101">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b48e9-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="b48e9-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility.</span><span class="sxs-lookup"><span data-stu-id="b48e9-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b48e9-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b48e9-103">Change description</span></span>

<span data-ttu-id="b48e9-104">V .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.</span><span class="sxs-lookup"><span data-stu-id="b48e9-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="b48e9-105">V rozhraní .NET Core není `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="b48e9-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b48e9-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b48e9-106">Version introduced</span></span>

<span data-ttu-id="b48e9-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="b48e9-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b48e9-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b48e9-108">Recommended action</span></span>

<span data-ttu-id="b48e9-109">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="b48e9-109">Remove the switch.</span></span> <span data-ttu-id="b48e9-110">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="b48e9-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="b48e9-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b48e9-111">Category</span></span>

<span data-ttu-id="b48e9-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b48e9-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b48e9-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b48e9-113">Affected APIs</span></span>

- <span data-ttu-id="b48e9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="b48e9-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937014"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="a7665-101">Přepínač kompatibility EnableVisualStyleValidation se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="a7665-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="a7665-102">V `Switch.System.Windows.Forms.EnableVisualStyleValidation` model Windows Forms .net Core 3,0 není podporován přepínač kompatibility.</span><span class="sxs-lookup"><span data-stu-id="a7665-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a7665-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a7665-103">Change description</span></span>

<span data-ttu-id="a7665-104">V .NET Framework přepínač `Switch.System.Windows.Forms.EnableVisualStyleValidation` kompatibility povolil aplikaci, aby odhlásila ověření vizuálních stylů zadaných v číselném tvaru.</span><span class="sxs-lookup"><span data-stu-id="a7665-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="a7665-105">V rozhraní .NET Core není `Switch.System.Windows.Forms.EnableVisualStyleValidation` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="a7665-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a7665-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a7665-106">Version introduced</span></span>

<span data-ttu-id="a7665-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a7665-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7665-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a7665-108">Recommended action</span></span>

<span data-ttu-id="a7665-109">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="a7665-109">Remove the switch.</span></span> <span data-ttu-id="a7665-110">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="a7665-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a7665-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a7665-111">Category</span></span>

<span data-ttu-id="a7665-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7665-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7665-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a7665-113">Affected APIs</span></span>

- <span data-ttu-id="a7665-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7665-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721265"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="5322e-101">Přepínač kompatibility UseLegacyImages se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5322e-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="5322e-102">`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5322e-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5322e-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5322e-103">Change description</span></span>

<span data-ttu-id="5322e-104">Počínaje .NET Framework 4,8 se přepínač kompatibility, který se `Switch.System.Windows.Forms.UseLegacyImages` zabývá možnostmi problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="5322e-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="5322e-105">Když je tato možnost nastavená na `true` , přepínač umožní uživateli obnovit starší verzi obrazu na vysokém rozlišení DPI, jejichž škálování je nastavené na větší než 100%.</span><span class="sxs-lookup"><span data-stu-id="5322e-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="5322e-106">Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="5322e-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="5322e-107">V rozhraní .NET Core není `Switch.System.Windows.Forms.UseLegacyImages` přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="5322e-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5322e-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5322e-108">Version introduced</span></span>

<span data-ttu-id="5322e-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5322e-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5322e-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5322e-110">Recommended action</span></span>

<span data-ttu-id="5322e-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="5322e-111">Remove the switch.</span></span> <span data-ttu-id="5322e-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="5322e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="5322e-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5322e-113">Category</span></span>

<span data-ttu-id="5322e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5322e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5322e-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5322e-115">Affected APIs</span></span>

- <span data-ttu-id="5322e-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="5322e-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181793"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="a2f98-101">Přepínač kompatibility. System. Windows. Forms. UseLegacyImages není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="a2f98-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="a2f98-102">Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4,8, není podporován v model Windows Forms v rozhraní .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a2f98-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a2f98-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="a2f98-103">Change description</span></span>

<span data-ttu-id="a2f98-104">Počínaje .NET Framework 4,8 se přepínač kompatibility, `Switch.System.Windows.Forms.UseLegacyImages` který se zabývá možnostmi problémy s škálováním obrazu ve scénářích ClickOnce v prostředích s vysokým rozlišením DPI.</span><span class="sxs-lookup"><span data-stu-id="a2f98-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="a2f98-105">Když je tato `true`možnost nastavená na, přepínač umožní uživateli obnovit starší verzi obrazu na vysokém rozlišení DPI, jejichž škálování je nastavené na větší než 100%.</span><span class="sxs-lookup"><span data-stu-id="a2f98-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="a2f98-106">Další informace najdete v [poznámkách k verzi .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="a2f98-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="a2f98-107">V rozhraní .NET Core `Switch.System.Windows.Forms.UseLegacyImages` není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="a2f98-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a2f98-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a2f98-108">Version introduced</span></span>

<span data-ttu-id="a2f98-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a2f98-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a2f98-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a2f98-110">Recommended action</span></span>

<span data-ttu-id="a2f98-111">Odeberte přepínač.</span><span class="sxs-lookup"><span data-stu-id="a2f98-111">Remove the switch.</span></span> <span data-ttu-id="a2f98-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="a2f98-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a2f98-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a2f98-113">Category</span></span>

<span data-ttu-id="a2f98-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2f98-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a2f98-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a2f98-115">Affected APIs</span></span>

- <span data-ttu-id="a2f98-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a2f98-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

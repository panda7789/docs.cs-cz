---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937117"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="64f1a-101">Přepínač kompatibility UseLegacyImages není podporován.</span><span class="sxs-lookup"><span data-stu-id="64f1a-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="64f1a-102">Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl zaveden v rozhraní .NET Framework 4.8, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.</span><span class="sxs-lookup"><span data-stu-id="64f1a-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64f1a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="64f1a-103">Change description</span></span>

<span data-ttu-id="64f1a-104">Počínaje rozhraním .NET Framework 4.8, přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility řeší možné problémy s škálováním obrázků ve scénářích ClickOnce v prostředích s vysokým dpi.</span><span class="sxs-lookup"><span data-stu-id="64f1a-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="64f1a-105">Pokud je `true`přepínač nastaven na , umožňuje uživateli obnovit změnu velikosti starších bitů na displejích s vysokým rozlišením DPI, jejichž měřítko je nastaveno na více než 100 %.</span><span class="sxs-lookup"><span data-stu-id="64f1a-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="64f1a-106">Další informace najdete [v tématu .NET Framework 4.8 Poznámky k verzi](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="64f1a-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="64f1a-107">V rozhraní .NET `Switch.System.Windows.Forms.UseLegacyImages` Core není přepínač podporován.</span><span class="sxs-lookup"><span data-stu-id="64f1a-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64f1a-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="64f1a-108">Version introduced</span></span>

<span data-ttu-id="64f1a-109">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="64f1a-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64f1a-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="64f1a-110">Recommended action</span></span>

<span data-ttu-id="64f1a-111">Odstraňte spínač.</span><span class="sxs-lookup"><span data-stu-id="64f1a-111">Remove the switch.</span></span> <span data-ttu-id="64f1a-112">Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="64f1a-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="64f1a-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="64f1a-113">Category</span></span>

<span data-ttu-id="64f1a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64f1a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64f1a-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64f1a-115">Affected APIs</span></span>

- <span data-ttu-id="64f1a-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="64f1a-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

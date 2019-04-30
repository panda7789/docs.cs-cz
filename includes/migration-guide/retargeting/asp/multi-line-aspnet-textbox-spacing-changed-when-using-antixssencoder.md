---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639438"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="263b1-101">Při použití AntiXSSEncoderu se měnily mezery ve víceřádkových textových polích ASP.Net</span><span class="sxs-lookup"><span data-stu-id="263b1-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

|   |   |
|---|---|
|<span data-ttu-id="263b1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="263b1-102">Details</span></span>|<span data-ttu-id="263b1-103">V rozhraní .NET Framework 4.0 se při používání nástroje <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name> během zpětného vystavení mezi řádky víceřádkového textového pole vkládaly řádky navíc.</span><span class="sxs-lookup"><span data-stu-id="263b1-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>.</span></span> <span data-ttu-id="263b1-104">V rozhraní .NET Framework 4.5 tato nadbytečná zalomení řádku nejsou, ale pouze v případě, že i webová aplikace cílí na verzi .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="263b1-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>|
|<span data-ttu-id="263b1-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="263b1-105">Suggestion</span></span>|<span data-ttu-id="263b1-106">Mějte na paměti, že u webových aplikací z verze 4.0, u nichž bylo změněno cílení na verzi .NET Framework 4.5, se můžou víceřádková textová pole vylepšit tím, že už se do nich nevkládají nadbytečná zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="263b1-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="263b1-107">Pokud to není žádoucí, můžete v aplikaci dosáhnout starého chování tak, že ji spustíte v rozhraní .NET Framework 4.5 a budete cílit na verzi .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="263b1-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>|
|<span data-ttu-id="263b1-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="263b1-108">Scope</span></span>|<span data-ttu-id="263b1-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="263b1-109">Minor</span></span>|
|<span data-ttu-id="263b1-110">Version</span><span class="sxs-lookup"><span data-stu-id="263b1-110">Version</span></span>|<span data-ttu-id="263b1-111">4.5</span><span class="sxs-lookup"><span data-stu-id="263b1-111">4.5</span></span>|
|<span data-ttu-id="263b1-112">Type</span><span class="sxs-lookup"><span data-stu-id="263b1-112">Type</span></span>|<span data-ttu-id="263b1-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="263b1-113">Retargeting</span></span>|

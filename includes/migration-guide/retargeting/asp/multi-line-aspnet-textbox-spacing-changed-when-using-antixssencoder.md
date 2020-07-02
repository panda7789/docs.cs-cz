---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617184"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="70dcd-101">Při použití AntiXSSEncoderu se měnily mezery ve víceřádkových textových polích ASP.Net</span><span class="sxs-lookup"><span data-stu-id="70dcd-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="70dcd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="70dcd-102">Details</span></span>

<span data-ttu-id="70dcd-103">V rozhraní .NET Framework 4.0 se při používání nástroje <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName> během zpětného vystavení mezi řádky víceřádkového textového pole vkládaly řádky navíc.</span><span class="sxs-lookup"><span data-stu-id="70dcd-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="70dcd-104">V rozhraní .NET Framework 4.5 tato nadbytečná zalomení řádku nejsou, ale pouze v případě, že i webová aplikace cílí na verzi .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="70dcd-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70dcd-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="70dcd-105">Suggestion</span></span>

<span data-ttu-id="70dcd-106">Mějte na paměti, že u webových aplikací z verze 4.0, u nichž bylo změněno cílení na verzi .NET Framework 4.5, se můžou víceřádková textová pole vylepšit tím, že už se do nich nevkládají nadbytečná zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="70dcd-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="70dcd-107">Pokud to není žádoucí, můžete v aplikaci dosáhnout starého chování tak, že ji spustíte v rozhraní .NET Framework 4.5 a budete cílit na verzi .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="70dcd-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="70dcd-108">Name</span><span class="sxs-lookup"><span data-stu-id="70dcd-108">Name</span></span>    | <span data-ttu-id="70dcd-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70dcd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70dcd-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="70dcd-110">Scope</span></span>   | <span data-ttu-id="70dcd-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="70dcd-111">Minor</span></span>       |
| <span data-ttu-id="70dcd-112">Verze</span><span class="sxs-lookup"><span data-stu-id="70dcd-112">Version</span></span> | <span data-ttu-id="70dcd-113">4.5</span><span class="sxs-lookup"><span data-stu-id="70dcd-113">4.5</span></span>         |
| <span data-ttu-id="70dcd-114">Typ</span><span class="sxs-lookup"><span data-stu-id="70dcd-114">Type</span></span>    | <span data-ttu-id="70dcd-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="70dcd-115">Retargeting</span></span> |

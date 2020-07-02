---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615634"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="0224e-101">ClickOnce podporuje SHA-256 na 4,0 cílené aplikace</span><span class="sxs-lookup"><span data-stu-id="0224e-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="0224e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0224e-102">Details</span></span>

<span data-ttu-id="0224e-103">Dříve aplikace ClickOnce s certifikátem podepsaným SHA-256 by vyžadovala, aby byla k dispozici .NET Framework 4,5 nebo novější, i když aplikace cílí na 4,0.</span><span class="sxs-lookup"><span data-stu-id="0224e-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="0224e-104">Nyní .NET Framework 4,0 cílené aplikace ClickOnce mohou běžet na .NET Framework 4,0 i v případě, že jsou podepsány pomocí algoritmu SHA-256.</span><span class="sxs-lookup"><span data-stu-id="0224e-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0224e-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="0224e-105">Suggestion</span></span>

<span data-ttu-id="0224e-106">Tato změna odstraní tuto závislost a povolí použití certifikátů SHA-256 k podepisování aplikací ClickOnce, které cílí na .NET Framework 4 a starší verze.</span><span class="sxs-lookup"><span data-stu-id="0224e-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="0224e-107">Name</span><span class="sxs-lookup"><span data-stu-id="0224e-107">Name</span></span>    | <span data-ttu-id="0224e-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0224e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0224e-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0224e-109">Scope</span></span>   | <span data-ttu-id="0224e-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="0224e-110">Minor</span></span>       |
| <span data-ttu-id="0224e-111">Verze</span><span class="sxs-lookup"><span data-stu-id="0224e-111">Version</span></span> | <span data-ttu-id="0224e-112">4.6</span><span class="sxs-lookup"><span data-stu-id="0224e-112">4.6</span></span>         |
| <span data-ttu-id="0224e-113">Typ</span><span class="sxs-lookup"><span data-stu-id="0224e-113">Type</span></span>    | <span data-ttu-id="0224e-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0224e-114">Retargeting</span></span> |

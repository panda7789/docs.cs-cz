---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804422"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="d3c8a-101">ClickOnce podporuje SHA-256 na 4.0-cílené aplikace</span><span class="sxs-lookup"><span data-stu-id="d3c8a-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d3c8a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d3c8a-102">Details</span></span>|<span data-ttu-id="d3c8a-103">Dříve clickonce aplikace s certifikátem podepsaným SHA-256 by vyžadovala .NET Framework 4.5 nebo novější, i když aplikace cílené 4.0.</span><span class="sxs-lookup"><span data-stu-id="d3c8a-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="d3c8a-104">Aplikace ClickOnce cílené na rozhraní .NET Framework 4.0 lze nyní spouštět v rozhraní .NET Framework 4.0, i když jsou podepsány sha-256.</span><span class="sxs-lookup"><span data-stu-id="d3c8a-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="d3c8a-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="d3c8a-105">Suggestion</span></span>|<span data-ttu-id="d3c8a-106">Tato změna odebere tuto závislost a povolí certifikáty SHA-256, které mají být použity k podpisu ClickOnce aplikace, které cílí na rozhraní .NET Framework 4 a starší verze.</span><span class="sxs-lookup"><span data-stu-id="d3c8a-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="d3c8a-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d3c8a-107">Scope</span></span>|<span data-ttu-id="d3c8a-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="d3c8a-108">Minor</span></span>|
|<span data-ttu-id="d3c8a-109">Version</span><span class="sxs-lookup"><span data-stu-id="d3c8a-109">Version</span></span>|<span data-ttu-id="d3c8a-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d3c8a-110">4.6</span></span>|
|<span data-ttu-id="d3c8a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d3c8a-111">Type</span></span>|<span data-ttu-id="d3c8a-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="d3c8a-112">Retargeting</span></span>|

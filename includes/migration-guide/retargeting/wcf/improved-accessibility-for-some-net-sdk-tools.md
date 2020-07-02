---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614549"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="d44d9-101">Vylepšené usnadnění pro některé nástroje .NET SDK</span><span class="sxs-lookup"><span data-stu-id="d44d9-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="d44d9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d44d9-102">Details</span></span>

<span data-ttu-id="d44d9-103">V sadě .NET Framework SDK 4.7.1 byly vylepšené nástroje SvcConfigEditor.exe a SvcTraceViewer.exe tím, že opravuje různé problémy s přístupností.</span><span class="sxs-lookup"><span data-stu-id="d44d9-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="d44d9-104">Většina z nich byla malé problémy, jako je název, který není definován, nebo některé vzorce automatizace uživatelského rozhraní nejsou správně implementovány.</span><span class="sxs-lookup"><span data-stu-id="d44d9-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="d44d9-105">I když mnoho uživatelů by si tyto nesprávné hodnoty nedozvěděli, zákazníci, kteří používají asistenční technologie, jako jsou čtečky obrazovky, budou tyto nástroje sady SDK k dispozici podrobněji.</span><span class="sxs-lookup"><span data-stu-id="d44d9-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="d44d9-106">V některých případech tyto opravy mění předchozí chování, jako je například pořadí fokusu klávesnice. Chcete-li získat všechny opravy usnadnění v těchto nástrojích, můžete do souboru app.config následující:</span><span class="sxs-lookup"><span data-stu-id="d44d9-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="d44d9-107">Name</span><span class="sxs-lookup"><span data-stu-id="d44d9-107">Name</span></span>    | <span data-ttu-id="d44d9-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d44d9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d44d9-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d44d9-109">Scope</span></span>   | <span data-ttu-id="d44d9-110">Edge</span><span class="sxs-lookup"><span data-stu-id="d44d9-110">Edge</span></span>        |
| <span data-ttu-id="d44d9-111">Verze</span><span class="sxs-lookup"><span data-stu-id="d44d9-111">Version</span></span> | <span data-ttu-id="d44d9-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d44d9-112">4.7.1</span></span>       |
| <span data-ttu-id="d44d9-113">Typ</span><span class="sxs-lookup"><span data-stu-id="d44d9-113">Type</span></span>    | <span data-ttu-id="d44d9-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="d44d9-114">Retargeting</span></span> |

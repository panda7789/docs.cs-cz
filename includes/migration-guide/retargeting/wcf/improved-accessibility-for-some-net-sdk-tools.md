---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760205"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="748d7-101">Vylepšení přístupnosti pro některé nástroje sady .NET SDK</span><span class="sxs-lookup"><span data-stu-id="748d7-101">Improved accessibility for some .NET SDK tools</span></span>

|   |   |
|---|---|
|<span data-ttu-id="748d7-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="748d7-102">Details</span></span>|<span data-ttu-id="748d7-103">V SDK rozhraní .NET Framework 4.7.1 byly vylepšeny nástroje SvcConfigEditor.exe a SvcTraceViewer.exe opravou různých usnadnění.</span><span class="sxs-lookup"><span data-stu-id="748d7-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="748d7-104">Většina z nich byly malé problémy, jako je název nedefinují nebo určité vzory pro automatizaci uživatelského rozhraní nebyl správně implementována.</span><span class="sxs-lookup"><span data-stu-id="748d7-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="748d7-105">Při nesprávné hodnoty si nevšimnou mnoho uživatelů, zákazníci, kteří používají podpůrnou technologií, jako je čtečky obrazovky najdete tyto sady SDK nástroje přístupnější.</span><span class="sxs-lookup"><span data-stu-id="748d7-105">While many users wouldn’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="748d7-106">Tyto opravy jistě, změňte některá předchozí chování, stejně jako pořadí fokus klávesnice. Zajistí všechno, co přístupnost opravy v těchto nástrojů můžete do souboru app.config následující:</span><span class="sxs-lookup"><span data-stu-id="748d7-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="748d7-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="748d7-107">Scope</span></span>|<span data-ttu-id="748d7-108">Edge</span><span class="sxs-lookup"><span data-stu-id="748d7-108">Edge</span></span>|
|<span data-ttu-id="748d7-109">Version</span><span class="sxs-lookup"><span data-stu-id="748d7-109">Version</span></span>|<span data-ttu-id="748d7-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="748d7-110">4.7.1</span></span>|
|<span data-ttu-id="748d7-111">Type</span><span class="sxs-lookup"><span data-stu-id="748d7-111">Type</span></span>|<span data-ttu-id="748d7-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="748d7-112">Retargeting</span></span>|


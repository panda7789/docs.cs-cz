---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803623"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="54f7b-101">Hostitelské ovládací prvky spravovaného prohlížeče v rozhraní .NET Framework 1.1 a 2.0 jsou zablokované.</span><span class="sxs-lookup"><span data-stu-id="54f7b-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

|   |   |
|---|---|
|<span data-ttu-id="54f7b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54f7b-102">Details</span></span>|<span data-ttu-id="54f7b-103">Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="54f7b-103">Hosting these controls is blocked in Internet Explorer.</span></span>|
|<span data-ttu-id="54f7b-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="54f7b-104">Suggestion</span></span>|<span data-ttu-id="54f7b-105">Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="54f7b-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="54f7b-106">Předchozí chování lze obnovit nastavením hodnoty EnableIEHosting podklíče registru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> k <code>1</code> pro x86 systémy a pro 32bitové procesy v x64 systémů a tím, že nastavíte <code>EnableIEHosting</code> podklíče registru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>k <code>1</code> pro 64bitové procesy v x64 systémy.</span><span class="sxs-lookup"><span data-stu-id="54f7b-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>|
|<span data-ttu-id="54f7b-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="54f7b-107">Scope</span></span>|<span data-ttu-id="54f7b-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="54f7b-108">Minor</span></span>|
|<span data-ttu-id="54f7b-109">Version</span><span class="sxs-lookup"><span data-stu-id="54f7b-109">Version</span></span>|<span data-ttu-id="54f7b-110">4.5</span><span class="sxs-lookup"><span data-stu-id="54f7b-110">4.5</span></span>|
|<span data-ttu-id="54f7b-111">Type</span><span class="sxs-lookup"><span data-stu-id="54f7b-111">Type</span></span>|<span data-ttu-id="54f7b-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="54f7b-112">Runtime</span></span>|

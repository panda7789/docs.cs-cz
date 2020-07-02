---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620071"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="4e701-101">Spravované prohlížeče hostující ovládací prvky z .NET Framework 1,1 a 2,0 jsou blokované</span><span class="sxs-lookup"><span data-stu-id="4e701-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="4e701-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4e701-102">Details</span></span>

<span data-ttu-id="4e701-103">Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4e701-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e701-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="4e701-104">Suggestion</span></span>

<span data-ttu-id="4e701-105">Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="4e701-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="4e701-106">Předchozí chování lze obnovit nastavením hodnoty EnableIEHosting podklíče registru pro <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> <code>1</code> systémy x86 a 32 procesy v systémech x64 a nastavením <code>EnableIEHosting</code> hodnoty podklíče registru na <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> <code>1</code> 64 procesy v systémech x64.</span><span class="sxs-lookup"><span data-stu-id="4e701-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="4e701-107">Name</span><span class="sxs-lookup"><span data-stu-id="4e701-107">Name</span></span>    | <span data-ttu-id="4e701-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4e701-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4e701-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4e701-109">Scope</span></span>   |<span data-ttu-id="4e701-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="4e701-110">Minor</span></span>|
|<span data-ttu-id="4e701-111">Verze</span><span class="sxs-lookup"><span data-stu-id="4e701-111">Version</span></span>|<span data-ttu-id="4e701-112">4.5</span><span class="sxs-lookup"><span data-stu-id="4e701-112">4.5</span></span>|
|<span data-ttu-id="4e701-113">Typ</span><span class="sxs-lookup"><span data-stu-id="4e701-113">Type</span></span>|<span data-ttu-id="4e701-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4e701-114">Runtime</span></span>|

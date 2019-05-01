---
title: Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6c20a69894c95086dbd813601ac8811ab4f337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985696"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="15a63-102">Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="15a63-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="15a63-103">Tato část popisuje rozhraní, která nespravovaných hostitelů můžete použít k integraci common language runtime (CLR) v rozhraní .NET Framework verze 1.0 a 1.1 do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="15a63-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="15a63-104">Tato rozhraní poskytuje metody pro hostitele konfigurace a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="15a63-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15a63-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="15a63-105">In This Section</span></span>  
 <span data-ttu-id="15a63-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="15a63-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="15a63-107">Poskytuje metody pro hostitele konfigurace <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="15a63-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="15a63-108">ICeeFileGen – třída</span><span class="sxs-lookup"><span data-stu-id="15a63-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="15a63-109">(Nepoužívané) Poskytuje funkce pro vytváření nativní přenosný spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="15a63-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="15a63-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15a63-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="15a63-111">Poskytuje metody pro hostitele a zadejte nastavení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="15a63-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15a63-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="15a63-112">Related Sections</span></span>  
 [<span data-ttu-id="15a63-113">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="15a63-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="15a63-114">Obsahuje témata, která popisují rozhraní hostování, opatřeného rozhraní .NET Framework verze 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="15a63-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>

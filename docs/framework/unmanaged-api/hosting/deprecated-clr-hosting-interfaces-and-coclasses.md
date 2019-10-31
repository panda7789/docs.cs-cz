---
title: Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 08e193ed40c6538b62d8b1af0a8c41b4225f136b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138252"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="ad43a-102">Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ad43a-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="ad43a-103">Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) v .NET Framework verzích 1,0 a 1,1 do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ad43a-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="ad43a-104">Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="ad43a-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad43a-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ad43a-105">In This Section</span></span>  
 <span data-ttu-id="ad43a-106">IAppDomainSetup –</span><span class="sxs-lookup"><span data-stu-id="ad43a-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="ad43a-107">Poskytuje metody pro hostitele ke konfiguraci <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ad43a-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="ad43a-108">ICeeFileGen – třída</span><span class="sxs-lookup"><span data-stu-id="ad43a-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="ad43a-109">Zastaralé Poskytuje funkce pro vytvoření nativního přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="ad43a-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="ad43a-110">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad43a-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="ad43a-111">Poskytuje metody pro hostitele ke konfiguraci nastavení CLR.</span><span class="sxs-lookup"><span data-stu-id="ad43a-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad43a-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ad43a-112">Related Sections</span></span>  
 [<span data-ttu-id="ad43a-113">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ad43a-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="ad43a-114">Obsahuje témata, která popisují rozhraní pro hostování poskytovaná pomocí .NET Framework verze 2,0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="ad43a-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>

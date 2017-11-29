---
title: "Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4714183eb79a25639dae6824a1d27eb1ca6bb009
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="3e5a2-102">Zastaralá rozhraní a třídy typu Coclass rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="3e5a2-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="3e5a2-103">Tato část popisuje rozhraní, která nespravované hostitelů můžete použít k integraci common language runtime (CLR) v rozhraní .NET Framework verze 1.0 a 1.1 do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="3e5a2-104">Tato rozhraní poskytují metody pro hostitele ke konfiguraci a načtení modulu runtime do procesu.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e5a2-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3e5a2-105">In This Section</span></span>  
 <span data-ttu-id="3e5a2-106">Iappdomainsetup –</span><span class="sxs-lookup"><span data-stu-id="3e5a2-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="3e5a2-107">Poskytuje metody pro hostitele nakonfigurovat <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="3e5a2-108">Iceefilegen – třídy</span><span class="sxs-lookup"><span data-stu-id="3e5a2-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="3e5a2-109">(Nepoužívané) Poskytuje funkce pro vytváření nativní přenosné spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="3e5a2-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="3e5a2-110">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e5a2-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="3e5a2-111">Poskytuje metody pro hostitele ke konfiguraci nastavení CLR.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e5a2-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3e5a2-112">Related Sections</span></span>  
 [<span data-ttu-id="3e5a2-113">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="3e5a2-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="3e5a2-114">Obsahuje témata, která popisují rozhraní hostování součástí rozhraní .NET Framework verze 2.0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="3e5a2-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>

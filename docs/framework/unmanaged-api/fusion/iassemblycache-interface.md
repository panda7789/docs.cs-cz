---
title: "IAssemblyCache – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a>IAssemblyCache – rozhraní
Představuje globální mezipaměti sestavení pro použití technologie fusion.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateAssemblyCacheItem – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|Technologie fusion vyhrazené pro interní použití.|  
|[InstallAssembly – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|Nainstaluje zadaný sestavení v globální mezipaměti sestavení.|  
|[QueryAssemblyInfo – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|Získá požadovaná data o zadaném sestavení.|  
|[UninstallAssembly – metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|Odinstaluje zadaný sestavení z globální mezipaměti sestavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)

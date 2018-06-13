---
title: IAssemblyCache – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4302a73f9f077c2e1bf4f66c2b80ab025ae4a62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430580"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)

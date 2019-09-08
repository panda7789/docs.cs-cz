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
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796780"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache – rozhraní
Představuje globální mezipaměť sestavení pro použití technologií Fusion.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateAssemblyCacheItem – metoda](iassemblycache-createassemblycacheitem-method.md)|Získá odkaz na nový [IAssemblyCacheItem](iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger – metoda](iassemblycache-createassemblyscavenger-method.md)|Vyhrazeno pro interní použití technologií Fusion.|  
|[InstallAssembly – metoda](iassemblycache-installassembly-method.md)|Nainstaluje zadané sestavení do globální mezipaměti sestavení (GAC).|  
|[QueryAssemblyInfo – metoda](iassemblycache-queryassemblyinfo-method.md)|Načte požadovaná data o zadaném sestavení.|  
|[UninstallAssembly – metoda](iassemblycache-uninstallassembly-method.md)|Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)

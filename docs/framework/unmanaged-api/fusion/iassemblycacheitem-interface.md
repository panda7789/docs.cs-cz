---
title: IAssemblyCacheItem – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796708"
---
# <a name="iassemblycacheitem-interface"></a>IAssemblyCacheItem – rozhraní
Představuje jedno sestavení v globální mezipaměti sestavení (GAC).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AbortItem – metoda](iassemblycacheitem-abortitem-method.md)|Umožňuje sestavení v globální mezipaměti sestavení provést operace vyčištění před jeho uvolněním.|  
|[Commit – metoda](iassemblycacheitem-commit-method.md)|Potvrdí odkaz na sestavení v mezipaměti do paměti.|  
|[CreateStream – metoda](iassemblycacheitem-createstream-method.md)|Vytvoří datový proud se zadaným názvem a formátem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
- [IAssemblyCache – rozhraní](iassemblycache-interface.md)

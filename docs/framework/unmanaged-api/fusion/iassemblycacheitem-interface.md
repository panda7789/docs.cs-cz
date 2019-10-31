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
ms.openlocfilehash: 2493b5338824e1eab3f82a9023bbcced59a98fc8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134457"
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
- [IAssemblyCache – rozhraní](iassemblycache-interface.md)

---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973753"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold – metoda
  
 Získá hodnotu nakonfigurované prahové hodnoty haldy velkého objektu (LOH).   
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a>Parametry  
 `pThreshold` \
 mimo Prahová hodnota haldy pro velké objekty v bajtech.
  
## <a name="remarks"></a>Poznámky  
 Objekty větší než prahová hodnota haldy pro velké objekty budou přiděleny na haldu velkých objektů. Počínaje rozhraním .NET Core 3,0 je prahová hodnota haldy pro velké `pThreshold` objekty konfigurovatelná, bude obsahovat aktivní mezní velikost haldy pro velké objekty v bajtech.

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Viz také:
- [Rozhraní ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)


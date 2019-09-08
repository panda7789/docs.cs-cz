---
title: IAssemblyName::IsEqual – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796567"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual – metoda
Určuje `IAssemblyName`, zda je zadaný objekt [IAssemblyName](iassemblyname-interface.md) na základě zadaných příznaků porovnávání stejný.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pName`  
 pro Objekt, na který se má `IAssemblyName`porovnat. `IAssemblyName`  
  
 `dwCmpFlags`  
 pro Bitová kombinace hodnot [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , které ovlivňují porovnání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [Výčty pro fúze](fusion-enumerations.md)

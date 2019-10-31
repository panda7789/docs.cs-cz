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
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134309"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual – metoda
Určuje, zda je zadaný objekt [IAssemblyName](iassemblyname-interface.md) roven tomuto `IAssemblyName`na základě zadaných příznaků porovnávání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pName`  
 pro Objekt `IAssemblyName`, pro který chcete porovnat tento `IAssemblyName`.  
  
 `dwCmpFlags`  
 pro Bitová kombinace hodnot [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) , které ovlivňují porovnání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [Výčty pro fúze](fusion-enumerations.md)

---
title: IAssemblyName::GetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: b86828e01fb00b12feff2ed451793c240e16e240
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134382"
---
# <a name="iassemblynamegetproperty-method"></a>IAssemblyName::GetProperty – metoda
Získá ukazatel na vlastnost, na kterou odkazuje zadaný identifikátor vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `PropertyId`  
 pro Jedinečný identifikátor pro požadovanou vlastnost.  
  
 `pvProperty`  
 mimo Vrácená data vlastnosti.  
  
 `pcbProperty`  
 [in, out] Velikost `pvProperty`v bajtech.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyName – rozhraní](iassemblyname-interface.md)

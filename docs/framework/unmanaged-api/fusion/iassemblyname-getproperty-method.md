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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c297c2476cb35fef861cda77f4f6f536fd85557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428186"
---
# <a name="iassemblynamegetproperty-method"></a>IAssemblyName::GetProperty – metoda
Získá ukazatel na vlastnost odkazuje zadaný identifikátor vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `PropertyId`  
 [v] Jedinečný identifikátor pro požadovanou vlastnost.  
  
 `pvProperty`  
 [out] Data vrácená vlastnost.  
  
 `pcbProperty`  
 [ve out] Velikost v bajtech z `pvProperty`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IAssemblyName – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

---
title: IAssemblyName::SetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb04a97597982fdae7a68ba4f3ed4d7420b4189
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488146"
---
# <a name="iassemblynamesetproperty-method"></a>IAssemblyName::SetProperty – metoda
Nastaví hodnotu vlastnosti odkazuje zadaný identifikátor vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `PropertyId`  
 [in] Jedinečný identifikátor vlastnosti, jehož hodnota bude nastavena.  
  
 `pvProperty`  
 [in] Hodnota, na kterou odkazuje vlastnost `PropertyId`.  
  
 `cbProperty`  
 [in] Velikost v bajtech, z `pvProperty`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IAssemblyName – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)

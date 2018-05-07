---
title: IInstallReferenceItem::GetReference – metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6c64b98f3b5ab0445b076b0d3bacfaa398e26f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference – metoda
Získá odkazy [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura reprezentována to [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRefData`  
 [out] Vrácený `FUSION_INSTALL_REFERENCE` ukazatel.  
  
 `dwFlags`  
 [v] Vyhrazeno pro budoucí rozšíření. `dwFlags` musí být 0 (nula).  
  
 `pvReserved`  
 [v] Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IInstallReferenceItem – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [FUSION_INSTALL_REFERENCE – struktura](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

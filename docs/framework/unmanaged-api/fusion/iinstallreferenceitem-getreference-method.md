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
ms.openlocfilehash: cd0a554535122b81f5812102c7951f56b294796a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213360"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference – metoda
Získá ukazatel [fusion_install_reference –](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktura představovaného tímto rozhraním [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefData`  
 [out] Vrácený `FUSION_INSTALL_REFERENCE` ukazatele.  
  
 `dwFlags`  
 [in] Vyhrazeno pro budoucí rozšíření. `dwFlags` musí být 0 (nula).  
  
 `pvReserved`  
 [in] Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být referencí s hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IInstallReferenceItem – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE – struktura](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

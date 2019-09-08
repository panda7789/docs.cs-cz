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
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796391"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference – metoda
Získá ukazatel na strukturu [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) reprezentované tímto objektem [IInstallReferenceItem –](iinstallreferenceitem-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefData`  
 mimo Vrácený `FUSION_INSTALL_REFERENCE` ukazatel.  
  
 `dwFlags`  
 pro Vyhrazeno pro budoucí rozšíření. `dwFlags`musí mít hodnotu 0 (nula).  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved`musí se jednat o odkaz s hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IInstallReferenceItem – rozhraní](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE – struktura](fusion-install-reference-structure.md)

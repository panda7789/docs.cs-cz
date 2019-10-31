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
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131680"
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
 mimo Vrácený ukazatel `FUSION_INSTALL_REFERENCE`.  
  
 `dwFlags`  
 pro Vyhrazeno pro budoucí rozšíření. `dwFlags` musí být 0 (nula).  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IInstallReferenceItem – rozhraní](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE – struktura](fusion-install-reference-structure.md)

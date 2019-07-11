---
title: IInstallReferenceEnum::GetNextInstallReferenceItem – metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dd96b10b5ee2880e0f9ee18048ec8ba2ee0b5ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779056"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a>IInstallReferenceEnum::GetNextInstallReferenceItem – metoda
Získá ukazatel na další [iinstallreferenceitem –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objektů obsažených v tomto [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefItem`  
 [out] Vrácený `IInstallReferenceItem` ukazatele.  
  
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
- [IInstallReferenceEnum – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)

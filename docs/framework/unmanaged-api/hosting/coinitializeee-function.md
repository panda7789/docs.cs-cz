---
title: CoInitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131944"
---
# <a name="coinitializeee-function"></a>CoInitializeEE – funkce
Zajišťuje, aby byl spouštěcí modul společného jazykového modulu runtime načten do procesu. Tato funkce je zastaralá v .NET Framework 4. Místo toho použijte metodu [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFlags`  
 pro Jedna z konstant výčtu [COINITIEE –](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM definované v WinError. h a hodnoty v následující tabulce.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Spouštěcí modul byl úspěšně načten.|  
|S_FALSE|Spouštěcí modul je již načten.|  
|E_FAIL|Spouštěcí modul nelze načíst.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte prováděcí modul, pokud nebyl dříve načten.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

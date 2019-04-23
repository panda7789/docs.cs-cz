---
title: _EFN_GetManagedObjectName – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a95008d98436161ac919ef307273bc797519f15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080615"
---
# <a name="efngetmanagedobjectname-function"></a>_EFN_GetManagedObjectName – funkce
Získá název typu pomocí ukazatele zadaný spravovaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 [in] Ukazatel na klientovi ladění.  
  
 `objAddr`  
 [in] Ukazatel spravovaného objektu.  
  
 szName  
 [out] Název typu.  
  
 `cbName`  
 [out] Počet znaků, které jsou k dispozici ve vyrovnávací paměti řetězce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a 0x1000 kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** SOS_Stacktrace.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

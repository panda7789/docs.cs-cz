---
title: CLRCreateInstance – funkce
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9dc3f87ce727076d561923fe35495bbfe4419e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768123"
---
# <a name="clrcreateinstance-function"></a>CLRCreateInstance – funkce
Poskytuje jednu ze tří rozhraní: [Iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Jeden z identifikátorů tří tříd: Argumenty CLSID_CLRMetaHost CLSID_CLRMetaHostPolicy či CLSID_CLRDebugging.  
  
 `riid`  
 [in] Jeden z identifikátorů tři rozhraní (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy nebo IID_ICLRDebugging.  
  
 `ppInterface`  
 [out] Jeden ze tří rozhraní: [Iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`ppInterface` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny podporované kombinace pro `clsid` a `riid`.  
  
|`clsid`|`riid`|  
|--------------|------------|  
|CLSID_CLRMetaHost|IID_ICLRMetaHost|  
|CLSID_CLRMetaHostPolicy|IID_ICLRMetaHostPolicy|  
|CLSID_CLRDebugging|IID_ICLRDebugging|  
  
 Následující kód ukazuje, jak používat `CLRCreateInstance` zobrazíte všechny tři rozhraní:  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)

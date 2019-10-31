---
title: FExecuteInAppDomainCallback – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138185"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a>FExecuteInAppDomainCallback – ukazatel na funkci
Odkazuje na funkci, která je volána modulem CLR (Common Language Runtime) ke spuštění spravovaného kódu.  
  
 Tento ukazatel funkce je zastaralý v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 pro Ukazatel na neprůhlednou paměť přidělenou volajícímu, která obsahuje spravovaný kód, který má být proveden.  
  
 Přidělení a životnost této paměti jsou ovládány volajícím (to znamená CLR). Toto není spravovaná technologie CLR – paměť haldy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Knihovny Mscorwks. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

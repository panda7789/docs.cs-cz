---
title: _CorDllMain – funkce
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136969"
---
# <a name="_cordllmain-function"></a>\_funkce CorDllMain

Inicializuje modul CLR (Common Language Runtime), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení knihovny DLL a zahájí provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hInst`  
 pro Obslužná rutina instance načteného modulu.  
  
 `dwReason`  
 pro Určuje, proč je volána funkce vstupního bodu knihovny DLL. Tento parametr může být jedna z následujících hodnot: DLL\_PROCESS_ATTACH, DLL\_vlákna\_připojit, DLL\_vlákna\_připojit nebo knihovny DLL\_proces\_odpojení. Popisy těchto hodnot naleznete v dokumentaci k `DllMain` v sadě SDK platformy.  
  
 `lpReserved`  
 pro Nepoužívané.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací `true` pro úspěch a `false`, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL. U spustitelných sestavení volá zavaděč místo toho funkci [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) .  
  
 Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru DLL.  
  
Funkce `_CorDllMain` je volána přímo zavaděčem operačního systému.
  
 Další informace najdete v části poznámky v tématu [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Požadavky  

 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

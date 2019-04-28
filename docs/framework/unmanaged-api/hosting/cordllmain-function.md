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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666922"
---
# <a name="cordllmain-function"></a>\_CorDllMain Function

Inicializuje modul CLR (CLR), vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení DLL a zahájí vykonávání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hInst`  
 [in] Popisovač instance načteného modulu.  
  
 `dwReason`  
 [in] Označuje, proč je volána funkce vstupního bodu knihovny DLL. Tento parametr může být jeden z následujících hodnot: Knihovna DLL\_PROCESS_ATTACH, knihovny DLL\_vlákna\_připojit, knihovny DLL\_vlákna\_ATTACH nebo knihovny DLL\_procesu\_ODPOJIT. Popisy těchto hodnot, najdete v článku `DllMain` dokumentaci Platform SDK.  
  
 `lpReserved`  
 [in] Nevyužité.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí `true` k dosažení úspěchu a `false` Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL. Pro spustitelný soubor sestavení zavaděče volá [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) namísto toho funkci.  
  
 Zavaděč operačního systému volá tuto metodu, bez ohledu na vstupní bod uvedený v souboru knihovny DLL.  
  
`_CorDllMain` Funkce je volána přímo zavaděčem operačního systému.
  
 Další informace naleznete v části poznámky v [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tématu.  
  
## <a name="requirements"></a>Požadavky  

 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616603"
---
# <a name="_cordllmain-function"></a>\_CorDllMain – funkce

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
 pro Určuje, proč je volána funkce vstupního bodu knihovny DLL. Tento parametr může být jedna z následujících hodnot: DLL \_ PROCESS_ATTACH, \_ připojení vlákna dll \_ , \_ připojení vlákna DLL \_ nebo \_ odpojení procesu dll \_ . Popisy těchto hodnot naleznete v `DllMain` dokumentaci k sadě SDK platformy.  
  
 `lpReserved`  
 pro Nepoužívané.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda `true` se vrátí pro úspěch a `false` dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána zavaděčem operačního systému pro sestavení knihovny DLL. V případě spustitelných sestavení volá zavaděč místo toho funkci [ \_ CorExeMain](corexemain-function.md) .  
  
 Zavaděč operačního systému volá tuto metodu bez ohledu na vstupní bod zadaný v souboru DLL.  
  
`_CorDllMain`Funkce je volána přímo zavaděčem operačního systému.
  
 Další informace najdete v části poznámky v tématu [ \_ CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Požadavky  

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Globální statické funkce pro metadata](../metadata/metadata-global-static-functions.md)

---
title: PreBindAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: db3ba3380d1fc30a8f34683618b5cc326d7d1906
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123061"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx – funkce
Načte zobrazovaný název po zásadě pro sestavení.  
  
 Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppCtx`  
 pro Identifikuje kontext aplikace.  
  
 `pName`  
 pro Určuje název sestavení.  
  
 `pAsmParent`  
 pro Identifikuje nadřazené sestavení. Tento parametr je ignorován.  
  
 `pwzRuntimeVersion`  
 pro Určuje verzi modulu runtime.  
  
 `ppNamePostPolicy`  
 mimo Obsahuje zobrazovaný název po zásadě.  
  
 `pvReserved`  
 pro Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
## <a name="remarks"></a>Poznámky  
 Výstupní parametr `ppNamePostPolicy` je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH. V opačném případě má hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d3e2535851d39be642de56a86b78c328ecaf446
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx – funkce
Získá po zásady zobrazovaný název sestavení.  
  
 Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppCtx`  
 [v] Identifikuje kontext aplikace.  
  
 `pName`  
 [v] Určuje název sestavení.  
  
 `pAsmParent`  
 [v] Určuje nadřazený sestavení. Tento parametr je ignorován.  
  
 `pwzRuntimeVersion`  
 [v] Určuje verzi modulu runtime.  
  
 `ppNamePostPolicy`  
 [out] Obsahuje po zásady zobrazovaný název.  
  
 `pvReserved`  
 [v] Vyhrazeno pro budoucí rozšíření. `pvReserved` musí být odkaz s hodnotou null.  
  
## <a name="remarks"></a>Poznámky  
 `ppNamePostPolicy` Výstupní parametr je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH. Jinak má hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

---
title: "PreBindAssemblyEx – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9bd5cb6be2ccfd25d61a8a2f4347b384e1b2567
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [v] Vyhrazeno pro budoucí rozšíření. `pvReserved`musí být odkaz s hodnotou null.  
  
## <a name="remarks"></a>Poznámky  
 `ppNamePostPolicy` Výstupní parametr je nastaven pouze v případě, že funkce vrátí hodnotu HRESULT FUSION_E_REF_DEF_MISMATCH. Jinak má hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Fúze globálních statických funkcí](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

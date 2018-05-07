---
title: CreateAssemblyCache – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba4259ad9cdf4f56fd4c00b5c7e9ebfa8b7fe1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="createassemblycache-function"></a>CreateAssemblyCache – funkce
Získá ukazatel na nový [iassemblycache –](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instanci, která představuje globální mezipaměti sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAsmCache`  
 [out] Vrácený `IAssemblyCache` ukazatel.  
  
 `dwReserved`  
 [v] Vyhrazeno pro budoucí rozšíření. `dwReserved` musí být 0 (nula).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IAssemblyCache – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)

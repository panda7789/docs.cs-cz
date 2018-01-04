---
title: "IAssemblyCache::QueryAssemblyInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.QueryAssemblyInfo
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66e09f805b120239eef764b8cd61835e713e236c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachequeryassemblyinfo-method"></a>IAssemblyCache::QueryAssemblyInfo – metoda
Získá požadovaná data o zadaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [v] Příznaky definované v Fusion.idl. Podporovány jsou následující hodnoty:  
  
-   QUERYASMINFO_FLAG_VALIDATE (0X00000001)  
  
-   QUERYASMINFO_FLAG_GETSIZE (0X00000002)  
  
 `pszAssemblyName`  
 [v] Název sestavení, pro které budou načtena data.  
  
 `pAsmInfo`  
 [ve out] [Assembly_info –](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) struktura, která obsahuje data o sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IAssemblyCache – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)

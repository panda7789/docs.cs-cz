---
title: "GetAssemblyIdentityFromFile – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyIdentityFromFile
helpviewer_keywords: GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56d7fb4ee74e40ecd29ee276665ff43ab9fd56be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile – funkce
Získá odkazy `IUnknown` objekt se zadaným `IID` v sestavení v zadaná cesta k souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 [v] Platná cesta k požadované sestavení.  
  
 `riid`  
 [v] `IID` Rozhraní vrátit.  
  
 `ppIdentity`  
 [out] Ukazatel vrácený rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <<!--zzxref:IUnknown --> `IUnknown`>  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

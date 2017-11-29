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
ms.openlocfilehash: 9f3374553df02193a6b726f37a53a929533e86cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Fúze globálních statických funkcí](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

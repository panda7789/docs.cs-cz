---
title: "IsFrameworkAssembly – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly – funkce
Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzAssemblyReference`  
 [v] Název sestavení, které chcete zkontrolovat.  
  
 `pbIsFrameworkAssembly`  
 [out] Logická hodnota, která určuje, jestli je sestavení spravuje.  
  
 `pwzFrameworkAssemblyIdentity`  
 [v] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.  
  
 `pccSize`  
 [v] Velikost `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Poznámky  
 `pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.  
  
 Pokud je toto sestavení součástí rozhraní .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat logickou hodnotu z `true`.  
  
 Pokud pojmenovaný sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` parametr není název sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu z `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

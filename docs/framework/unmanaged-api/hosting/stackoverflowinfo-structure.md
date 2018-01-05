---
title: "StackOverflowInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a880a7c30277d382bff2b46ebe10720880e907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo – struktura
Uloží typ přetečení, k níž došlo a informace na výjimku, která byla vydána z důvodu přetečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`soType`|Hodnota [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) výčet, který určuje typ přetečení.|  
|`pExceptionInfo`|Ukazatel na Win32 `EXCEPTION_POINTERS` objekt, který obsahuje záznam výjimky s popisem nezávislé na počítač výjimky a kontextu záznam s závislé na počítač popis kontext procesoru v okamžiku výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 A `StackOverflowInfo` je předán objekt [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu pro `Event_StackOverflow` události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)

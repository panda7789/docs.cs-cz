---
title: "CorLinkerOptions – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLinkerOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLinkerOptions
helpviewer_keywords: CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65914e52228bf55a35d48bfbf036c8bb78b29c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corlinkeroptions-enumeration"></a>CorLinkerOptions – výčet
Určuje příznaky výběr možností pro metadata linkeru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDAssembly`|Privátní typy a globální funkce nejsou zachována.|  
|`MDNetModule`|Privátní typy a globální funkce se zachovají.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

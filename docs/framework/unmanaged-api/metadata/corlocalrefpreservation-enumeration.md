---
title: "CorLocalRefPreservation – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c35bbfef62f65a9a401d00f9ae56e2f4c00bb0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corlocalrefpreservation-enumeration"></a>CorLocalRefPreservation – výčet
Obsahuje hodnot příznaku pro zpracování místní odkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|Zachovat žádné místní odkazy.|  
|`MDPreserveLocalTypeRef`|Zachovejte místního typu odkazy.|  
|`MDPreserveLocalMemberRef`|Zachovejte odkazy na místní členy.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

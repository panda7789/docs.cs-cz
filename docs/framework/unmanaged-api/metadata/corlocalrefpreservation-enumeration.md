---
title: CorLocalRefPreservation – výčet
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee808ba403a513b897134420b45ebe8cd3537571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442242"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

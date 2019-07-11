---
title: CeeSectionAttr – výčet
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61fc71c2ab0a9107f5e9fbb354fe0f8c2fb0dace
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776335"
---
# <a name="ceesectionattr-enumeration"></a>CeeSectionAttr – výčet
Obsahuje hodnoty, které určují atributy oddílu pro použití [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`sdNone`|Oddíl nemá žádné atributy.|  
|`sdReadOnly`|Oddíl obsahuje inicializovaná data, která lze pouze číst, nejsou aktualizována.|  
|`sdReadWrite`|Oddíl obsahuje inicializovaná data, která může číst nebo aktualizovat.|  
|`sdExecute`|Oddíl obsahuje spustitelný kód, který může číst a spustit.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

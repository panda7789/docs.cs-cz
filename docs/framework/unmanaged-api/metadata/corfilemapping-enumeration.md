---
title: CorFileMapping – výčet
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c8864aa604b0483130eac5aa0d7c0640abbac99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping – výčet
Obsahuje hodnoty, které popisují typ mapování souboru vrácená volání [imetadatainfo::getfilemapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`fmFlat`|Soubor je namapovaný jako datový soubor. To znamená `SEC_IMAGE` příznak nebyl předán Microsoft Win32 `CreateFileMapping` funkce.|  
|`fmExecutableImage`|Soubor je mapovaný pro spuštění, a to buď pomocí `LoadLibrary` funkce nebo `CreateFileMapping` fungovat s `SEC_IMAGE` příznak.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [GetFileMapping – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

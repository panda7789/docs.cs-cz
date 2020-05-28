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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007387"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping – výčet
Obsahuje hodnoty, které popisují typ mapování souboru, které je vráceno voláním metody [IMetaDataInfo –:: GetFileMapping –](imetadatainfo-getfilemapping-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`fmFlat`|Soubor je namapován jako datový soubor. To znamená, že `SEC_IMAGE` Příznak nebyl předán funkci Microsoft Win32 `CreateFileMapping` .|  
|`fmExecutableImage`|Soubor je namapován pro provedení pomocí `LoadLibrary` funkce nebo `CreateFileMapping` funkce s `SEC_IMAGE` příznakem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
- [GetFileMapping – metoda](imetadatainfo-getfilemapping-method.md)

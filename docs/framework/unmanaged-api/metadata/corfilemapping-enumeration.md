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
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450291"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping – výčet
Obsahuje hodnoty, které popisují typ mapování souboru, které je vráceno voláním metody [IMetaDataInfo –:: GetFileMapping –](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`fmFlat`|Soubor je namapován jako datový soubor. To znamená, že příznak `SEC_IMAGE` nebyl předán funkci Microsoft Win32 `CreateFileMapping`.|  
|`fmExecutableImage`|Soubor je namapovaný pro provedení pomocí funkce `LoadLibrary` nebo funkce `CreateFileMapping` s příznakem `SEC_IMAGE`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [GetFileMapping – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

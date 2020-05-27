---
title: CorPEKind – výčet
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007556"
---
# <a name="corpekind-enumeration"></a>CorPEKind – výčet
Obsahuje hodnoty, které popisují přenositelný spustitelný soubor (PE), vrácený voláním metody [IMetaDataImport2:: GetPEKind –](imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`peNot`|Označuje, že se nejedná o soubor PE.|  
|`peILOnly`|Označuje, že tento soubor PE obsahuje pouze spravovaný kód.|  
|`pe32BitRequired`|Označuje, že tento soubor PE provede volání Win32.|  
|`pe32Plus`|Označuje, že tento soubor PE běží na 64 platformě.|  
|`pe32Unmanaged`|Označuje, že tento soubor PE je nativní kód.|  
|pe32BitPreferred|Označuje, že tento soubor PE je neutrální pro platformu a upřednostňuje, aby se načetla v 32 bitovém prostředí.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty lze použít v bitových kombinacích.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)

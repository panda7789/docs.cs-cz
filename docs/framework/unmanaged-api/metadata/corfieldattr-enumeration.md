---
title: CorFieldAttr – výčet
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432e202eb8db105e8d56d3d36cdc8001bac5320c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182374"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr – výčet
Obsahuje hodnoty, které popisují metadata o pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`fdFieldAccessMask`|Určuje informace o usnadnění.|  
|`fdPrivateScope`|Určuje, že pole se nedá odkazovat.|  
|`fdPrivate`|Určuje, že pole je přístupná jenom pro jeho nadřazeného typu.|  
|`fdFamANDAssem`|Určuje, že pole je přístupné z odvozených tříd v jeho sestavení.|  
|`fdAssembly`|Určuje, že pole je přístupné pro všechny typy v sestavení.|  
|`fdFamily`|Určuje, že pole je přístupná jenom pro její typ a odvozené třídy.|  
|`fdFamORAssem`|Určuje, že pole je přístupný z odvozených tříd a všechny typy v sestavení.|  
|`fdPublic`|Určuje, že pole je přístupné pro všechny typy s viditelnost tohoto rozsahu.|  
|`fdStatic`|Určuje, že pole je členem jeho typu, nikoli člena instance.|  
|`fdInitOnly`|Určuje, že pole nelze změnit po inicializaci.|  
|`fdLiteral`|Určuje, že hodnota pole je konstantu kompilace.|  
|`fdNotSerialized`|Určuje, že pole není serializovat, když je její typ je vzdálený.|  
|`fdSpecialName`|Určuje, že pole je speciální a který odpovídá názvu jak.|  
|`fdPinvokeImpl`|Určuje, že implementace pole je dál prostřednictvím PInvoke.|  
|`fdReservedMask`|Modul common language runtime vyhrazené pro interní použití.|  
|`fdRTSpecialName`|Určuje, že common language runtime metadata interních rozhraních API by měla kontrolovat kódování názvu.|  
|`fdHasFieldMarshal`|Určuje, zda pole obsahuje zařazovací informace.|  
|`fdHasDefault`|Určuje, že pole má výchozí hodnotu.|  
|`fdHasFieldRVA`|Určuje, že pole má relativní virtuální adresu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

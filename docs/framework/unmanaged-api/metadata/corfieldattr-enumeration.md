---
title: "CorFieldAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5128ea59f7668737885835723156fc7f1786872
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
|`fdPrivateScope`|Určuje, že se nemůže odkazovat pole.|  
|`fdPrivate`|Určuje, že je dostupný pouze pomocí jeho nadřazený typ pole.|  
|`fdFamANDAssem`|Určuje, že pole je přístupné odvozené třídy v jeho sestavení.|  
|`fdAssembly`|Určuje, že pole je přístupný pro všechny typy v sestavení.|  
|`fdFamily`|Určuje, že pole je přístupné pouze její typ a odvozených třídách.|  
|`fdFamORAssem`|Určuje, že pole je přístupný odvozené třídy a všechny typy v sestavení.|  
|`fdPublic`|Určuje, že pole je přístupný pro všechny typy pomocí viditelnost tento obor.|  
|`fdStatic`|Určuje, že je pole členem její typ a nikoli instanci členu.|  
|`fdInitOnly`|Určuje, že pole nelze změnit po inicializaci.|  
|`fdLiteral`|Určuje, že hodnota pole je konstanta kompilaci.|  
|`fdNotSerialized`|Určuje, zda pole není serializovat, když jeho typ je vzdálený.|  
|`fdSpecialName`|Určuje, že pole je speciální a, jeho název popisuje jak.|  
|`fdPinvokeImpl`|Určuje, že je pomocí služby PInvoke dál implementace pole.|  
|`fdReservedMask`|Modul common language runtime vyhrazené pro interní použití.|  
|`fdRTSpecialName`|Určuje, že běžná metadata modulu runtime jazyka interní rozhraní API měli kontrolovat kódování názvu.|  
|`fdHasFieldMarshal`|Určuje, že pole obsahuje zařazování informace.|  
|`fdHasDefault`|Určuje, zda pole má výchozí hodnotu.|  
|`fdHasFieldRVA`|Určuje, zda má pole relativní virtuální adresu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

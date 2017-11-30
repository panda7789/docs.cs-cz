---
title: "CorMethodAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodAttr
helpviewer_keywords: CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91afbc9894826b1f44d84f23b550a81d610e3de9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr – výčet
Obsahuje hodnoty, které popisují funkce metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`mdMemberAccessMask`|Určuje přístup ke členu.|  
|`mdPrivateScope`|Určuje, že člena nelze odkazovat.|  
|`mdPrivate`|Určuje, že je přístupná jenom pro nadřazený typ člena.|  
|`mdFamANDAssem`|Určuje, že je člen přístupný podtypů pouze v tomto sestavení.|  
|`mdAssem`|Určuje, že je člen v accessibly každému uživateli v sestavení.|  
|`mdFamily`|Určuje, že je dostupný pouze podle typu a podtypů člena.|  
|`mdFamORAssem`|Určuje, že je člen přístupný odvozené třídy a dalších typů v jeho sestavení.|  
|`mdPublic`|Určuje, že je člen přístupné všechny typy s přístupem k oboru.|  
|`mdStatic`|Určuje, zda člen je definován v rámci typu, nikoli jako člen instance.|  
|`mdFinal`|Určuje, že metoda nelze přepsat.|  
|`mdVirtual`|Určuje, zda lze přepsat metodu.|  
|`mdHideBySig`|Určuje, že metoda skryje podle názvu a podpis, nikoli jen název.|  
|`mdVtableLayoutMask`|Určuje rozložení virtuální tabulky.|  
|`mdReuseSlot`|Určuje, že slotu použít pro tuto metodu v tabulce virtuální znovu použít. Toto nastavení je výchozí.|  
|`mdNewSlot`|Určuje, že metoda vždy získá nový slot v tabulce virtuálních.|  
|`mdCheckAccessOnOverride`|Určuje, že metoda se dá přepsat stejné typy, pro které je viditelná.|  
|`mdAbstract`|Určuje, že metoda není implementována.|  
|`mdSpecialName`|Určuje, že metoda je speciální a že její název popisuje jak.|  
|`mdPinvokeImpl`|Určuje, že metoda implementace je dál pomocí služby PInvoke.|  
|`mdUnmanagedExport`|Určuje, že metoda je spravovaný metoda exportovat na nespravovaný kód.|  
|`mdReservedMask`|Modul common language runtime vyhrazené pro interní použití.|  
|`mdRTSpecialName`|Určuje, že by měl modul common language runtime kontrolovat kódování název metody.|  
|`mdHasSecurity`|Určuje, že metoda má zabezpečení s ním spojená.|  
|`mdRequireSecObject`|Určuje, že metoda volá jinou metodu obsahující zabezpečovací kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

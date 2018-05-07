---
title: CorMethodImpl – výčet
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4bb91423b2eaeda7d945cf14553609fd33ce9b0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl – výčet
Obsahuje hodnoty, které popisují způsob implementace funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`miCodeTypeMask`|Příznaky, které popisují typ kódu.|  
|`miIL`|Určuje, že je metoda implementace Microsoft (MSIL intermediate language).|  
|`miNative`|Určuje, že je nativní implementace metod.|  
|`miOPTIL`|Určuje, že je metoda implementace OPTIL.|  
|`miRuntime`|Určuje, že implementace metod poskytuje modul common language runtime.|  
|`miManagedMask`|Příznaky, které označuje, zda kód je spravované nebo nespravované.|  
|`miUnmanaged`|Určuje, že je metoda implementace nespravované.|  
|`miManaged`|Určuje, že je spravovaný implementace metod.|  
|`miForwardRef`|Určuje, že metoda je definována. Tento příznak se používá hlavně ve scénářích sloučení.|  
|`miPreserveSig`|Určuje, zda podpis metody nemůže být pro konverzi HRESULT pozměněny.|  
|`miInternalCall`|Modul common language runtime vyhrazené pro interní použití.|  
|`miSynchronized`|Určuje, že metoda je jednovláknové prostřednictvím jeho obsahu.|  
|`miNoInlining`|Určuje, že metoda nemůže být vložená.|  
|`miAggressiveInlining`|Určuje, že metoda by měla být vložená Pokud je to možné.|  
|`miNoOptimization`|Určuje, že by neměl být optimalizována metodu.|  
|`miMaxMethodImplVal`|Maximální hodnota platná `CorMethodImpl`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

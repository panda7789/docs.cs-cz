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
ms.openlocfilehash: b32e8f0b03ef6d550c384f3d932cc295a7270028
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007660"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl – výčet
Obsahuje hodnoty, které popisují funkce implementace metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`miCodeTypeMask`|Příznaky, které popisují typ kódu.|  
|`miIL`|Určuje, že implementace metody je Microsoft Intermediate Language (MSIL).|  
|`miNative`|Určuje, že implementace metody je nativní.|  
|`miOPTIL`|Určuje, že implementace metody je OPTI.|  
|`miRuntime`|Určuje, že implementace metody je poskytována modulem CLR (Common Language Runtime).|  
|`miManagedMask`|Příznaky, které označují, zda je kód spravovaný nebo nespravovaný.|  
|`miUnmanaged`|Určuje, že implementace metody není spravována.|  
|`miManaged`|Určuje, že je spravovaná implementace metody.|  
|`miForwardRef`|Určuje, že je metoda definovaná. Tento příznak se používá hlavně ve scénářích sloučení.|  
|`miPreserveSig`|Určuje, že signatura metody nemůže být pozměněná pro konverzi HRESULT.|  
|`miInternalCall`|Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).|  
|`miSynchronized`|Určuje, že metoda je jediným vláknem přes jeho tělo.|  
|`miNoInlining`|Určuje, že metoda nemůže být vložená.|  
|`miAggressiveInlining`|Určuje, že by měla být metoda vložená, pokud je to možné.|  
|`miNoOptimization`|Určuje, že by neměla být optimalizována metoda.|  
|`miMaxMethodImplVal`|Maximální platná hodnota pro `CorMethodImpl` .|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)

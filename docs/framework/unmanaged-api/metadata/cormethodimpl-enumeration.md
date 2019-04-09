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
ms.openlocfilehash: 2138dd32cf39db7b7c8989ba5827178d1a1e46c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117232"
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
|`miIL`|Určuje, že implementace metody je jazyk Microsoft intermediate language (MSIL).|  
|`miNative`|Určuje, že je nativní implementace metody.|  
|`miOPTIL`|Určuje, že implementace metody OPTIL.|  
|`miRuntime`|Určuje, že implementace metody poskytuje modul common language runtime.|  
|`miManagedMask`|Příznaky, které označují, zda kód je spravovaná nebo nespravovaná.|  
|`miUnmanaged`|Určuje, že implementace metody nespravované.|  
|`miManaged`|Určuje, že je spravovaná implementace metody.|  
|`miForwardRef`|Určuje, že metoda je definována. Tento příznak se používá především ve scénářích sloučení.|  
|`miPreserveSig`|Určuje, že podpis metody nemůže být pozměnění pro konverzi HRESULT.|  
|`miInternalCall`|Modul common language runtime vyhrazené pro interní použití.|  
|`miSynchronized`|Určuje, že metoda je jednovláknový prostřednictvím svého těla.|  
|`miNoInlining`|Určuje, že metoda nemůže být vložená.|  
|`miAggressiveInlining`|Určuje, že metoda by měla být vložit. Pokud je to možné.|  
|`miNoOptimization`|Určuje, že metoda neměl optimalizovat.|  
|`miMaxMethodImplVal`|Největší platná hodnota pro `CorMethodImpl`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

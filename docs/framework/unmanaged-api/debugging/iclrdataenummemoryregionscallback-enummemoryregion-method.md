---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122939"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda
Volá se [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) , aby se do ladicího programu nahlásila výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Počáteční adresa oblasti paměti, ve které se má vytvořit výčet.  
  
 `size`  
 pro Velikost oblasti paměti (v bajtech).  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ICLRDataEnumMemoryRegions::EnumMemoryRegions` vyvolá tuto metodu zpětného volání po každém pokusu o vytvoření výčtu oblasti paměti. Výčet bude pokračovat i v případě, že tato metoda vrátí hodnotu HRESULT indikující selhání.  
  
 Oblasti hlášené tímto zpětným voláním můžou být duplicitní nebo překrývající se oblasti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataEnumMemoryRegionsCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)

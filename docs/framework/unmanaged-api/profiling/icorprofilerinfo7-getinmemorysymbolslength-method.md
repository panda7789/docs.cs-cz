---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength – metoda'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495435"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: GetInMemorySymbolsLength – metoda
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Vrátí délku datového proudu symbolů v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro Identifikátor modulu, který obsahuje datový proud v paměti.  
  
 pCountSymbolBytes  
 mimo Ukazatel na `DWORD` hodnotu, která, když metoda vrátí, obsahuje délku datového proudu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí `S_OK` , zda lze určit délku paměťového proudu, i když je hodnota nulová (0).  
  
 Metoda vrátí, `CORPROF_E_MODULE_IS_DYNAMIC` zda byla metoda vytvořena pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="remarks"></a>Poznámky  
 Pokud má modul symboly v paměti, je délka datového proudu umístěna v `pCountSymbolBytes` . Pokud modul neobsahuje symboly v paměti, `*pCountSymbolBytes = 0` .  
  
> [!NOTE]
> Aktuální implementace nepodporuje reflexe. Emit. Pokud byl modul vytvořen pomocí reflexe. Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](icorprofilerinfo7-interface.md)

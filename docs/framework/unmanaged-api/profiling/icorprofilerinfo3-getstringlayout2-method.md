---
title: ICorProfilerInfo3::GetStringLayout2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496370"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 – metoda
Získá informace o rozložení objektu řetězce. Tato metoda nahrazuje metodu [ICorProfilerInfo2:: GetStringLayout –](icorprofilerinfo2-getstringlayout-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStringLengthOffset`  
 mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku samotného řetězce. Délka je uložena jako `DWORD` .  
  
 `pBufferOffset`  
 mimo Ukazatel na posun vyrovnávací paměti vzhledem k `ObjectID` ukazateli, který ukládá řetězec velkých znaků.  
  
## <a name="remarks"></a>Poznámky  
 Řetězce můžou nebo nemusí být zakončené znakem null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)

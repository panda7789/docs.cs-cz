---
title: ICorProfilerInfo2::GetStringLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 71e2bc1d60e050d817429db5bc6926b3b16c637c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431404"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout – metoda
Získá informace o rozložení objektu řetězce. Tato metoda je zastaralá v .NET Framework 4 a nahrazuje se metodou [ICorProfilerInfo3:: getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 mimo Ukazatel na posun umístění vzhledem k ukazateli `ObjectID`, který ukládá délku řetězce. Délka je uložena jako `DWORD`.  
  
> [!NOTE]
> Tento parametr vrátí délku samotného řetězce, nikoli délku vyrovnávací paměti. Délka vyrovnávací paměti již není k dispozici.  
  
 `PStringLengthOffset`  
 mimo Ukazatel na posun umístění vzhledem k ukazateli `ObjectID`, který ukládá délku samotného řetězce. Délka je uložena jako `DWORD`.  
  
 `pBufferOffset`  
 mimo Ukazatel na posun vyrovnávací paměti vzhledem k ukazateli `ObjectID`, který ukládá řetězec velkých znaků.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetStringLayout` získá posuny relativní k ukazateli `ObjectID` na místech, kde jsou uložena následující:  
  
- Délka vyrovnávací paměti řetězce.  
  
- Délka samotného řetězce.  
  
- Vyrovnávací paměť, která obsahuje skutečný řetězec velkých znaků.  
  
 Řetězce můžou být zakončené znakem null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

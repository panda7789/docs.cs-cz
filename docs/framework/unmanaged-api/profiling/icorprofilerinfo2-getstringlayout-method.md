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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa5ecf63ac3795a58369d94f9fb15f853edb576
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490708"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout – metoda
Získá informace o rozložení objektu string. Tato metoda je zastaralé v rozhraní .NET Framework 4 a je nahrazen technologií [icorprofilerinfo3::getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 [out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku řetězce. Délka se ukládá jako `DWORD`.  
  
> [!NOTE]
>  Tento parametr vrátí délku řetězce, nikoli délka vyrovnávací paměti. Délka vyrovnávací paměti je už k dispozici.  
  
 `PStringLengthOffset`  
 [out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku samotný řetězec. Délka se ukládá jako `DWORD`.  
  
 `pBufferOffset`  
 [out] Ukazatel na posun vyrovnávací paměti, relativní k `ObjectID` ukazatel, který ukládá řetězec širokých znaků.  
  
## <a name="remarks"></a>Poznámky  
 `GetStringLayout` Metoda získá posuny, vzhledem k `ObjectID` ukazatele z umístění, ve kterých se ukládají následující:  
  
- Délka vyrovnávací paměti řetězce.  
  
- Délka samotný řetězec.  
  
- Vyrovnávací paměť, která obsahuje skutečné řetězec širokých znaků.  
  
 Řetězce můžou být zakončený hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

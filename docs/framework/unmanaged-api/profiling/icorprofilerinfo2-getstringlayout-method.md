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
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963795"
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
 mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku řetězce. Délka je uložena jako `DWORD`.  
  
> [!NOTE]
> Tento parametr vrátí délku samotného řetězce, nikoli délku vyrovnávací paměti. Délka vyrovnávací paměti již není k dispozici.  
  
 `PStringLengthOffset`  
 mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku samotného řetězce. Délka je uložena jako `DWORD`.  
  
 `pBufferOffset`  
 mimo Ukazatel na posun vyrovnávací paměti vzhledem k `ObjectID` ukazateli, který ukládá řetězec znaků v šířce.  
  
## <a name="remarks"></a>Poznámky  
 Metoda získá posuny relativní vzhledem `ObjectID` k ukazateli umístění, ve kterých jsou uloženy následující: `GetStringLayout`  
  
- Délka vyrovnávací paměti řetězce.  
  
- Délka samotného řetězce.  
  
- Vyrovnávací paměť, která obsahuje skutečný řetězec velkých znaků.  
  
 Řetězce můžou být zakončené znakem null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

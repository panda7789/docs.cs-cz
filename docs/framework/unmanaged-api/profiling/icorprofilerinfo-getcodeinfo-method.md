---
title: ICorProfilerInfo::GetCodeInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 583189cd667af142ab7d0934be34411644dac936
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863917"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo – metoda
Získá rozsah nativního kódu přidruženého k zadanému ID funkce.  
  
 Tato metoda je zastaralá. Místo toho použijte metodu [ICorProfilerInfo2:: GetCodeInfo2 –](icorprofilerinfo2-getcodeinfo2-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, ke které je přidružen nativní kód.  
  
 `pStart`  
 mimo Ukazatel na pole bajtů, které tvoří nativní kód funkce.  
  
 `pcSize`  
 mimo Ukazatel na celé číslo, které určuje velikost (v bajtech) nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Za účelem optimalizace výkonu je modul runtime ve .NET Framework verze 2,0 rozdělen do více oblastí předkompilovaným nativním kódem funkce. V důsledku toho je metoda `GetCodeInfo` v .NET Framework 2,0 zastaralá, protože není schopna zpracovat rozsah nativního kódu funkce. Profilery by se měly místo toho přepnout na použití obecnější metody `ICorProfilerInfo2::GetCodeInfo2`.  
  
 Tato funkce používá vyrovnávací paměti přidělené volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,0  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)

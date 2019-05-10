---
title: ICorProfilerInfo2::GetThreadStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de0e46f4703479daeb96cb83276ec14150125e7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587433"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress – metoda
Získá adresu zadané pole vlákna, která je v rámci zadaného vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] ID třídy, která obsahuje požadovaná pole statická na úrovni vlákna.  
  
 `fieldToken`  
 [in] Token metadat pro požadované pole statická na úrovni vlákna.  
  
 `threadId`  
 [in] ID vlákna, která je v oboru pro požadovaný statické pole.  
  
 `ppAddress`  
 [out] Ukazatel na adresu statické pole, která je v rámci zadaného vlákna.  
  
## <a name="remarks"></a>Poznámky  
 `GetThreadStaticAddress` Metoda může vrátit jednu z následujících akcí:  
  
- CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.  
  
- Adresy objektů, které mohou být v haldě uvolňování paměti. Tyto adresy můžou stát neplatnými po uvolnění paměti, takže se po uvolňování paměti kolekce profilovací programy by neměl předpokládají, že jsou platné.  
  
 Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé statická pole může již být inicializován a kořenová objekty uvolnění paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

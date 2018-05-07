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
ms.openlocfilehash: a38c8323157cee866ac0ecab97532b9b72a932b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress – metoda
Získá adresu zadaného pole statické přístup z více vláken, který je v rozsahu zadaný vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy, která obsahuje požadovaná pole statické přístup z více vláken.  
  
 `fieldToken`  
 [v] Token metadata pro požadované pole statické přístup z více vláken.  
  
 `threadId`  
 [v] ID podprocesu, který je v rozsahu pro požadovaný statické pole.  
  
 `ppAddress`  
 [out] Ukazatel na adresu statické pole, které je v rámci zadaného vlákno.  
  
## <a name="remarks"></a>Poznámky  
 `GetThreadStaticAddress` Metoda může vrátit jednu z následujících:  
  
-   HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.  
  
-   Adresy objekty, které mohou být v kolekci halda paměti. Tyto adresy může zneplatní po uvolňování paměti, takže po profilery kolekce paměti by neměl předpokládat jsou platné.  
  
 Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

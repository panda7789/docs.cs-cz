---
title: "ICorProfilerInfo2::GetContextStaticAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e92435927203bb2a75ff92d883470832126da080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress – metoda
Získá adresu pro zadaný kontext statické pole, která je v rozsahu zadaný kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy, která obsahuje požadovanou kontextu statické pole.  
  
 `fieldToken`  
 [v] Token metadata pro požadované pole kontextu statické.  
  
 `contextId`  
 [v] ID kontext, který je v rozsahu pro požadované pole kontextu statické.  
  
 `ppAddress`  
 [out] Ukazatel na adresu statické pole, která je v rámci zadaného kontextu.  
  
## <a name="remarks"></a>Poznámky  
 `GetContextStaticAddress` Metoda může vrátit jednu z následujících:  
  
-   HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.  
  
-   Adresy objekty, které mohou být v kolekci halda paměti. Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.  
  
 Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

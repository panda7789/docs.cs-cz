---
title: ICorProfilerInfo2::GetAppDomainStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8e1886a3e33b533eb525f5b35480a8a7d326da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454589"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress – metoda
Získá adresu domény statické pole určená aplikace, které je v oboru domény zadané aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy třídy, která obsahuje pole domény statické požadovaná aplikace.  
  
 `fieldToken`  
 [v] Token metadata pro domény statické pole požadovaná aplikace.  
  
 `appDomainId`  
 [v] ID domény aplikace, které je v rozsahu pro požadovaný statické pole.  
  
 `ppAddress`  
 [out] Ukazatel na adresu statického pole, která je v rámci domény zadané aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `GetAppDomainStaticAddress` Metoda může vrátit jednu z následujících:  
  
-   HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.  
  
-   Adresy objekty, které mohou být v kolekci halda paměti. Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.  
  
 Před dokončením konstruktoru třídy třídy `GetAppDomainStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

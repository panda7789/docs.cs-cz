---
title: ICorProfilerInfo3::GetThreadStaticAddress2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: ee44c89ec30edcb6233081f0757fa0f7b7191178
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449642"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>ICorProfilerInfo3::GetThreadStaticAddress2 – metoda
Získá adresu zadaného pole statického vlákna, které je v oboru zadaného vlákna a domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 pro ID třídy, která obsahuje požadované pole se statickým vláknem.  
  
 `fieldToken`  
 pro Token metadat pro požadované pole se statickým vláknem  
  
 `appDomainId`  
 pro ID domény aplikace  
  
 `threadId`  
 pro ID vlákna, které je oborem požadovaného statického pole.  
  
 `ppAddress`  
 mimo Ukazatel na adresu statického pole, které je v zadaném vlákně.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetThreadStaticAddress2` může vracet jednu z následujících možností:  
  
- CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.  
  
- Adresy objektů, které mohou být v haldě uvolňování paměti. Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.  
  
 Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress2` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.  
  
 Metoda [ICorProfilerInfo2:: GetThreadStaticAddress –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) je podobná metodě `GetThreadStaticAddress2`, ale nepřijímá argument domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)

---
title: ICorProfilerInfo2::GetClassIDInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b98746be189e211572e5517aac1f06825973b39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779779"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 – metoda
Získá nadřazený modulu a metadata token pro definici otevřený obecný zadanou třídu, `ClassID` své nadřazené třídy a `ClassID` pro každý typ argumentu, pokud jsou k dispozici třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] ID třídy, pro kterou budou načteny informace.  
  
 `pModuleId`  
 [out] Ukazatel na ID nadřazeného modulu pro definici otevřený obecný dané třídy.  
  
 `pTypeDefToken`  
 [out] Ukazatel na token metadat pro definici otevřený obecný dané třídy.  
  
 `pParentClassId`  
 [out] Ukazatel na ID nadřazené třídy.  
  
 `cNumTypeArgs`  
 [in] Velikost `typeArgs` pole.  
  
 `pcNumTypeArgs`  
 [out] Ukazatel na celkový počet elementů k dispozici.  
  
 `typeArgs`  
 [out] Pole `ClassID` hodnot, z nichž každý představuje ID argument typu třídy. Po návratu metody `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassIDInfo2` Metoda je podobná [icorprofilerinfo::getclassidinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metody, ale `GetClassIDInfo2` získá další informace o obecném typu.  
  
 Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daný modul. Token metadat, který je vrácen do umístění odkazuje `pTypeDefToken` lze použít k přístupu k metadatům pro třídu.  
  
 Po `GetClassIDInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `ClassID` hodnoty. K tomuto účelu porovnat hodnoty, které `pcNumTypeArgs` odkazuje na hodnotu `cNumTypeArgs` parametru. Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělte větší `typeArgs` vyrovnávací paměti, aktualizujte `cNumTypeArgs` nové, větší velikosti a volání `GetClassIDInfo2` znovu.  
  
 Alternativně můžete nejprve volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit `typeArgs` velikost k hodnotě vrácené ve vyrovnávací paměti `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)

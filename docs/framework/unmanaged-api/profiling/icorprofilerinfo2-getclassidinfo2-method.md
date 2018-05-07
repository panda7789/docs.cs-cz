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
ms.openlocfilehash: 2af0eacbff8220be7f2286f7f345f14126972261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 – metoda
Získá nadřazený modulu a metadata token pro definici otevřený obecný pro zadanou třídu, `ClassID` ze své nadřízené třídy a `ClassID` pro každý typ argumentu, pokud existuje, třídy.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] ID třídy, pro které budou načteny informace.  
  
 `pModuleId`  
 [out] Ukazatel na ID nadřazeného modulu pro definici otevřený obecný pro zadanou třídu.  
  
 `pTypeDefToken`  
 [out] Ukazatel na token metadata pro definici otevřený obecný pro zadanou třídu.  
  
 `pParentClassId`  
 [out] Ukazatel na ID nadřazené třídy.  
  
 `cNumTypeArgs`  
 [v] Velikost `typeArgs` pole.  
  
 `pcNumTypeArgs`  
 [out] Ukazatel na celkový počet elementů k dispozici.  
  
 `typeArgs`  
 [out] Pole `ClassID` hodnoty, z nichž každý představuje ID argument typu třídy. Po návratu metody `typeArgs` bude obsahovat některé nebo všechny dostupných `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassIDInfo2` Metoda je podobná [icorprofilerinfo::getclassidinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metoda, ale `GetClassIDInfo2` získá další informace o obecného typu.  
  
 Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daného modulu. Metadata token, který je vrácen do umístění odkazuje `pTypeDefToken` pak lze získat přístup k metadatům pro třídu.  
  
 Po `GetClassIDInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `ClassID` hodnoty. K tomuto účelu porovnat hodnotu, `pcNumTypeArgs` body s hodnotou `cNumTypeArgs` parametr. Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělit větší `typeArgs` vyrovnávací paměti, aktualizujte `cNumTypeArgs` s novou, větší velikost a volání `GetClassIDInfo2` znovu.  
  
 Alternativně můžete nejdřív volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Pak můžete nastavit `typeArgs` velikost k hodnotě vrácené ve vyrovnávací paměti `pcNumTypeArgs` a volání `GetClassIDInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)

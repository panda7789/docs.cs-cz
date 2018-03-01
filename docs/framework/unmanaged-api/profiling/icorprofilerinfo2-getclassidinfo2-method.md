---
title: "ICorProfilerInfo2::GetClassIDInfo2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)

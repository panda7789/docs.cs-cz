---
title: ICorProfilerInfo2::GetFunctionInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a864d8285c311a9d5c41a425f81678b294f0d8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460535"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 – metoda
Získá nadřazené třídy, metadata token a `ClassID` každý typ argumentu, pokud je k dispozici funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] ID funkce, pro které chcete získat nadřazené třídy a další informace.  
  
 `frameInfo`  
 [v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.  
  
 `pClassId`  
 [out] Ukazatel na nadřazené třídy funkce.  
  
 `pModuleId`  
 [out] Ukazatel na modul, ve kterém je definovaný funkce nadřazené třídy.  
  
 `pToken`  
 [out] Ukazatel na token metadata pro funkci.  
  
 `cTypeArgs`  
 [v] Velikost `typeArgs` pole.  
  
 `pcTypeArgs`  
 [out] Ukazatel na celkový počet `ClassID` hodnoty.  
  
 `typeArgs`  
 [out] Pole `ClassID` hodnoty, z nichž každý je ID argumentu typu funkce. Po návratu metody `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daného modulu. Metadata token, který je vrácen do umístění odkazuje `pToken` pak lze získat přístup k metadatům pro funkci.  
  
 Třída ID a zadejte argumenty, které jsou vráceny prostřednictvím `pClassId` a `typeArgs` parametry závisí na hodnota, je předaná `frameInfo` parametr, jak je znázorněno v následující tabulce.  
  
|Hodnota `frameInfo` parametr|Výsledek|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` hodnotu, který byl získán z `FunctionEnter2` zpětného volání|`ClassID`, Vrácený v umístění odkazuje `pClassId`, a všechny argumenty, vrátí se v typů `typeArgs` pole, bude přesný.|  
|A `COR_PRF_FRAME_INFO` který byl získán z zdroje jiné než `FunctionEnter2` zpětného volání|Přesné `ClassID` a argumenty typu nelze určit. To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.|  
|Nula|Přesné `ClassID` a argumenty typu nelze určit. To znamená `ClassID` může mít hodnotu null a může mít některé argumenty typu zpět jako <xref:System.Object>.|  
  
 Po `GetFunctionInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `ClassID` hodnoty. K tomuto účelu porovnat hodnotu, `pcTypeArgs` body s hodnotou `cTypeArgs` parametr. Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělený velikost `ClassID` hodnotu, přidělit větší `pcTypeArgs` vyrovnávací paměti, aktualizujte `cTypeArgs` s novou, větší velikost a volání `GetFunctionInfo2` znovu.  
  
 Alternativně můžete nejdřív volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcTypeArgs` dělený velikost `ClassID` hodnota a volání `GetFunctionInfo2` znovu.  
  
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

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
ms.openlocfilehash: 45a7e0c793baa31d9efde2763570cd46a072fe86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546316"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 – metoda
Získá na nadřazenou třídu tokenu metadat a `ClassID` každý typ argumentu, pokud jsou k dispozici funkce.  
  
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
 [in] ID funkce, pro které chcete-li získat nadřazené třídu a další informace.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámec zásobníku.  
  
 `pClassId`  
 [out] Ukazatel na nadřazené třídy funkce.  
  
 `pModuleId`  
 [out] Ukazatel na modul, ve kterém je definována funkce nadřazené třídy.  
  
 `pToken`  
 [out] Ukazatel na token metadat pro funkci.  
  
 `cTypeArgs`  
 [in] Velikost `typeArgs` pole.  
  
 `pcTypeArgs`  
 [out] Ukazatel na celkový počet `ClassID` hodnoty.  
  
 `typeArgs`  
 [out] Pole `ClassID` hodnot, z nichž každý je ID argument typu funkce. Po návratu metody `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daný modul. Token metadat, který je vrácen do umístění odkazuje `pToken` lze použít k přístupu k metadatům pro funkci.  
  
 Třída ID a typ argumentů, které jsou vráceny prostřednictvím `pClassId` a `typeArgs` parametry záviset na hodnotě předané `frameInfo` parametru, jak je znázorněno v následující tabulce.  
  
|Hodnota `frameInfo` parametr|Výsledek|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` hodnoty, který byl získán z `FunctionEnter2` zpětného volání|`ClassID`, Vracet v umístění odkazuje `pClassId`, a všechny argumenty, vrácené v typu `typeArgs` pole, nebudou přesné.|  
|A `COR_PRF_FRAME_INFO` , který byl získán ze zdroje jiné než `FunctionEnter2` zpětného volání|Přesné `ClassID` a argumenty typu nelze určit. To znamená `ClassID` může mít hodnotu null a některé argumenty typu by mohl pocházet zpět jako <xref:System.Object>.|  
|Nula|Přesné `ClassID` a argumenty typu nelze určit. To znamená `ClassID` může mít hodnotu null a některé argumenty typu by mohl pocházet zpět jako <xref:System.Object>.|  
  
 Po `GetFunctionInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `ClassID` hodnoty. K tomuto účelu porovnat hodnoty, které `pcTypeArgs` odkazuje na hodnotu `cTypeArgs` parametru. Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` rozdělené podle velikosti `ClassID` hodnoty, přidělte větší `pcTypeArgs` vyrovnávací paměti, aktualizujte `cTypeArgs` nové, větší velikosti a volání `GetFunctionInfo2` znovu.  
  
 Alternativně můžete nejprve volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcTypeArgs` rozdělené podle velikosti `ClassID` hodnotu a volání `GetFunctionInfo2` znovu.  
  
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

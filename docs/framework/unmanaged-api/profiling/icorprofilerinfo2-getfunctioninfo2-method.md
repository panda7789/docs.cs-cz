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
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433187"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 – metoda
Získá nadřazenou třídu, token metadat a `ClassID` každého argumentu typu, pokud je k dispozici funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 pro ID funkce, pro kterou se má získat nadřazená třída a další informace  
  
 `frameInfo`  
 pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku.  
  
 `pClassId`  
 mimo Ukazatel na nadřazenou třídu funkce.  
  
 `pModuleId`  
 mimo Ukazatel na modul, ve kterém je definována nadřazená třída funkce.  
  
 `pToken`  
 mimo Ukazatel na token metadat pro funkci.  
  
 `cTypeArgs`  
 pro Velikost pole `typeArgs`.  
  
 `pcTypeArgs`  
 mimo Ukazatel na celkový počet `ClassID`ch hodnot.  
  
 `typeArgs`  
 mimo Pole hodnot `ClassID`, z nichž každý je ID argumentu funkce. Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) pro daný modul. Token metadat, který je vrácen do umístění odkazovaného `pToken` lze následně použít pro přístup k metadatům funkce.  
  
 IDENTIFIKÁTOR třídy a argumenty typu, které jsou vráceny pomocí `pClassId` a parametry `typeArgs` závisí na hodnotě předané v parametru `frameInfo`, jak je znázorněno v následující tabulce.  
  
|Hodnota parametru `frameInfo`|Výsledek|  
|----------------------------------------|------------|  
|Hodnota `COR_PRF_FRAME_INFO` získaná z zpětného volání `FunctionEnter2`|`ClassID`vrácená v umístění, na které odkazuje `pClassId`a všechny argumenty typu vrácené v poli `typeArgs`, budou přesně.|  
|`COR_PRF_FRAME_INFO` získaný ze zdroje jiného než zpětné volání `FunctionEnter2`|Nelze určit přesný `ClassID` a argumenty typu. To znamená, že `ClassID` může mít hodnotu null a některé argumenty typu se mohou vrátit jako <xref:System.Object>.|  
|Nula|Nelze určit přesný `ClassID` a argumenty typu. To znamená, že `ClassID` může mít hodnotu null a některé argumenty typu se mohou vrátit jako <xref:System.Object>.|  
  
 Jakmile `GetFunctionInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `typeArgs` dostatečně velká, aby obsahovala všechny `ClassID` hodnoty. To provedete tak, že porovnáte hodnotu, na kterou `pcTypeArgs` odkazuje, hodnotou `cTypeArgs` parametru. Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělená velikostí `ClassID` hodnoty, přidělte větší vyrovnávací paměť `pcTypeArgs`, aktualizujte `cTypeArgs` o novou, větší velikost a zavolejte `GetFunctionInfo2` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu vrácenou v `pcTypeArgs` dělenou velikostí `ClassID` a volat `GetFunctionInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)

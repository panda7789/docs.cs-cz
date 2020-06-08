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
ms.openlocfilehash: f5438ddc655f0f6a7c11d978a47b1bf9e2a13059
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497000"
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
 pro `COR_PRF_FRAME_INFO`Hodnota, která odkazuje na informace o snímku zásobníku.  
  
 `pClassId`  
 mimo Ukazatel na nadřazenou třídu funkce.  
  
 `pModuleId`  
 mimo Ukazatel na modul, ve kterém je definována nadřazená třída funkce.  
  
 `pToken`  
 mimo Ukazatel na token metadat pro funkci.  
  
 `cTypeArgs`  
 pro Velikost `typeArgs` pole.  
  
 `pcTypeArgs`  
 mimo Ukazatel na celkový počet `ClassID` hodnot.  
  
 `typeArgs`  
 mimo Pole `ClassID` hodnot, z nichž každý je identifikátor argumentu typu funkce. Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../metadata/index.md) pro daný modul. Token metadat, který je vrácen do umístění odkazovaného pomocí, `pToken` lze následně použít pro přístup k metadatům funkce.  
  
 ID třídy a argumenty typu, které jsou vráceny prostřednictvím `pClassId` parametrů a `typeArgs` závisí na hodnotě předané v `frameInfo` parametru, jak je uvedeno v následující tabulce.  
  
|Hodnota `frameInfo` parametru|Výsledek|  
|----------------------------------------|------------|  
|`COR_PRF_FRAME_INFO`Hodnota, která byla získána z `FunctionEnter2` zpětného volání|`ClassID`, Vrácený v umístění, na který odkazuje `pClassId` , a všechny argumenty typu vrácené v poli `typeArgs` , budou přesně.|  
|A `COR_PRF_FRAME_INFO` získaný ze zdrojového jiného než `FunctionEnter2` zpětného volání|`ClassID`Nelze určit přesný a typové argumenty. To znamená, že `ClassID` může být null a některé argumenty typu se mohou vrátit jako <xref:System.Object> .|  
|Nula|`ClassID`Nelze určit přesný a typové argumenty. To znamená, že `ClassID` může být null a některé argumenty typu se mohou vrátit jako <xref:System.Object> .|  
  
 Po `GetFunctionInfo2` návratu je nutné ověřit, zda `typeArgs` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `ClassID` hodnoty. Provedete to tak, že porovnáte hodnotu, `pcTypeArgs` na kterou odkazuje, s hodnotou `cTypeArgs` parametru. Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělené velikostí `ClassID` hodnoty, přidělte větší `pcTypeArgs` vyrovnávací paměť, aktualizujte `cTypeArgs` novou, větší velikost a zavolejte `GetFunctionInfo2` znovu.  
  
 Případně můžete `GetFunctionInfo2` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `pcTypeArgs` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcTypeArgs` dělené velikostí `ClassID` hodnoty a volat `GetFunctionInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)

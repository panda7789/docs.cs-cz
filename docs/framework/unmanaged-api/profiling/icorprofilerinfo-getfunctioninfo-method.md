---
title: ICorProfilerInfo::GetFunctionInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: e7193526bb0da1d28da4bf6bde108fc4d3fba273
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503013"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo – metoda
Získá nadřazenou třídu a token metadat pro určenou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, pro kterou se má získat nadřazená třída a token metadat  
  
 `pClassId`  
 mimo Ukazatel na nadřazenou třídu funkce.  
  
 `pModuleId`  
 mimo Ukazatel na modul, ve kterém je definována nadřazená třída funkce.  
  
 `pToken`  
 mimo Ukazatel na token metadat pro funkci.  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní metadat pro daný modul. Token metadat, který je vrácen do umístění odkazovaného pomocí, `pToken` lze následně použít pro přístup k metadatům funkce.  
  
 `ClassID`Funkce na obecné třídě nemusí být získatelné bez dalších kontextových informací o použití funkce. V takovém případě `pClassId` bude 0. Kód profileru by měl používat [ICorProfilerInfo2:: GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou COR_PRF_FRAME_INFO k poskytnutí více kontextu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)

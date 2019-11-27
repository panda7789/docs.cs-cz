---
title: ICorProfilerInfo::GetClassIDInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: c3b1bdac8ccd37cf2f6aac5073def313f04acf28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439248"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a>ICorProfilerInfo::GetClassIDInfo – metoda
Získá nadřazený modul a token metadat pro určenou třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 pro ID třídy, pro kterou chcete získat informace.  
  
 `pModuleId`  
 mimo Ukazatel na ID nadřazeného modulu třídy.  
  
 `pTypeDefToken`  
 mimo Ukazatel na token metadat pro třídu.  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní metadat pro daný modul. Token metadat, který je vrácen do umístění odkazovaného `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.  
  
 Chcete-li získat další informace pro obecné typy, použijte [ICorProfilerInfo2:: GetClassIDInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

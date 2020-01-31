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
ms.openlocfilehash: 4b9c577fab91e9527a1edc6c93e0618c8fe4e662
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864066"
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
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní metadat pro daný modul. Token metadat, který je vrácen do umístění odkazovaného `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.  
  
 Chcete-li získat další informace pro obecné typy, použijte [ICorProfilerInfo2:: GetClassIDInfo2 –](icorprofilerinfo2-getclassidinfo2-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)

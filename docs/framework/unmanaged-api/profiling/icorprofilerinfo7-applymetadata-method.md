---
title: 'ICorProfilerInfo7:: ApplyMetaData – metoda'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: c30206145d08a22af49c4a6a0dc83fd7382bcc06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495503"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData – metoda
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Aplikuje metadata nově definovaná `IMetadataEmit::Define*` metodami na zadaný modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 pro Identifikátor modulu, jehož metadata se změnila.  
  
## <a name="remarks"></a>Poznámky  
 Pokud jsou změny metadat provedeny po zpětném volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) , je nutné před použitím nových metadat zavolat tuto metodu.  
  
 `ApplyMetaData`podporuje přidávání následujících typů metadat:  
  
- `AssemblyRef`záznamy, které vytvoříte voláním [IMetaDataAssemblyEmit::D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md). Metoda.  
  
- `TypeRef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec`záznamy, které vytvoříte voláním metody [IMetaDataEmit:: gettokenfromtypespec –](../metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec`záznamy, které vytvoříte voláním metody [IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) .  

Počínaje platformou .NET Core 3,0 `ApplyMetaData` podporuje také následující typy:

- `TypeDef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md) . Přidání virtuálních metod do existujícího typu však není podporováno. Před zpětným voláním [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) musí být virtuální metody přidané.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](icorprofilerinfo7-interface.md)

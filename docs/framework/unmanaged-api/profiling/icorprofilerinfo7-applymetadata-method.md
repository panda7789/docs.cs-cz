---
title: ICorProfilerInfo7::ApplyMetaData Method
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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861694"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData Method
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Aplikuje metadata nově definovaná metodami `IMetadataEmit::Define*` do zadaného modulu.  
  
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
  
 `ApplyMetaData` podporuje pouze přidávání následujících typů metadat:  
  
- `AssemblyRef` záznamy, které vytvoříte voláním metody [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). Metoda.  
  
- `TypeRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit:: gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .  

Počínaje rozhraním .NET Core 3,0 `ApplyMetaData` také podporuje následující typy:

- `TypeDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) . Přidání virtuálních metod do existujícího typu však není podporováno. Před zpětným voláním [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) musí být virtuální metody přidané.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](icorprofilerinfo7-interface.md)

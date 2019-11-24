---
title: IMetaDataAssemblyEmit::SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431946"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps – metoda
Modifies the specified `Assembly` metadata structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pma`  
 [in] The metadata token that specifies the `Assembly` metadata structure to be modified.  
  
 `pbPublicKey`  
 [in] A pointer to the public key of the publisher of the assembly.  
  
 `cbPublicKey`  
 [in] The size in bytes of `pbPublicKey`.  
  
 `ulHashAlgId`  
 [in] The identifier for the hash algorithm used to hash the assembly files.  
  
 `szName`  
 [in] The human-readable text name of the assembly.  
  
 `pMetaData`  
 [in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.  
  
 `dwAssemblyFlags`  
 [in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.  
  
## <a name="remarks"></a>Poznámky  
 To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.  
  
## <a name="requirements"></a>Požadavky  
 **Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

---
title: IMetaDataAssemblyEmit::DefineAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 20628e708261076c6e172ff30c366a0d69c2e0f2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432122"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly – metoda
Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKey`  
 [in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.  
  
 `cbPublicKey`  
 [in] The size in bytes of `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.  
  
 `szName`  
 [in] The human-readable text name of the assembly. This value must not exceed 1024 characters.  
  
 `pMetaData`  
 [in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.  
  
 `dwAssemblyFlags`  
 [in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.  
  
 `pmda`  
 [out] A pointer to the metadata token.  
  
## <a name="remarks"></a>Poznámky  
 Only one `Assembly` metadata structure can be defined within a manifest.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

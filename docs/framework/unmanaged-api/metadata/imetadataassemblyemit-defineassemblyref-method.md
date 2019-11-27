---
title: IMetaDataAssemblyEmit::DefineAssemblyRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: c88b7a401a19b1bd0e02edab7ef7bbee1372199e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432077"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef – metoda
Vytvoří strukturu `AssemblyRef` obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyOrToken`  
 pro Veřejný klíč vydavatele odkazovaného sestavení. Pomocná funkce [StrongNameTokenFromAssembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) se dá použít k získání hodnoty hash veřejného klíče, která se má předat jako tento parametr.  
  
 `cbPublicKeyOrToken`  
 pro Velikost v bajtech `pbPublicKeyOrToken`.  
  
 `szName`  
 pro Textový název sestavení čitelný lidmi Tato hodnota nesmí překročit 1024 znaků.  
  
 `pMetaData`  
 pro Instance AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí odkazovaného sestavení.  
  
 `pbHashValue`  
 pro Data algoritmu hash přidružená k odkazovanému sestavení Volitelné.  
  
 `cbHashValue`  
 pro Velikost v bajtech `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 pro Bitová kombinace hodnot [CorAssemblyFlags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) , která má vliv na chování prováděcího modulu.  
  
 `pmdar`  
 mimo Ukazatel na vrácený `AssemblyRef` token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Pro každé sestavení, na které odkazuje toto sestavení, musí být definována jedna `AssemblyRef` struktura metadat.  
  
 V době běhu jsou podrobnosti odkazovaného sestavení předány do překladače sestavení s označením, že představují informace "sestavené". Překladač sestavení následně aplikuje zásady.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

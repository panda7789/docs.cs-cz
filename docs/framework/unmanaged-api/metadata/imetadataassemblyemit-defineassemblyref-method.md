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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117349"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef – metoda
Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Veřejný klíč vydavatele odkazovaných sestavení. Pomocná funkce [strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) můžete použít k získání hodnota hash veřejného klíče předejte jako tento parametr.  
  
 `cbPublicKeyOrToken`  
 [in] Velikost v bajtech `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Uživatelsky čitelná textová název sestavení. Tato hodnota nesmí překročit 1024 znaků.  
  
 `pMetaData`  
 [in] Assemblymetadata – instance, který obsahuje informace o verzi, platformy a národní prostředí odkazovaného sestavení.  
  
 `pbHashValue`  
 [in] Hodnota hash data přidružená k odkazované sestavení. Volitelné.  
  
 `cbHashValue`  
 [in] Velikost v bajtech `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bitová kombinace hodnot [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které ovlivňují chování prováděcího modulu.  
  
 `pmdar`  
 [out] Ukazatel na vrácenou `AssemblyRef` token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `AssemblyRef` struktury metadat musí být definované pro jednotlivá sestavení, která toto sestavení odkazuje.  
  
 Podrobnosti o odkazovaném sestavení v době běhu, jsou předány překladač sestavení s údajem, že představují informace "jako předdefinovaný". Překladač sestavení potom použije zásady.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

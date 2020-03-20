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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177891"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly – metoda
Vytvoří `Assembly` strukturu obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.  
  
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
 [v] Veřejný klíč, který identifikuje vydavatele sestavení nebo NULL, pokud sestavení není silně pojmenované.  
  
 `cbPublicKey`  
 [v] Velikost v bajtů `pbPublicKey`.  
  
 `uHashAlgId`  
 [v] Identifikátor algoritmu hash, který se má použít k šifrování souborů v sestavení, nebo null pro určení algoritmu SHA-1.  
  
 `szName`  
 [v] Text čitelný pro člověka název sestavení. Tato hodnota nesmí překročit 1024 znaků.  
  
 `pMetaData`  
 [v] Ukazatel na instanci ASSEMBLYMETADATA, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.  
  
 `dwAssemblyFlags`  
 [v] Kombinace hodnot [CorAssemblyFlags,](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) které popisují prvky sestavy.  
  
 `pmda`  
 [out] Ukazatel na token metadat.  
  
## <a name="remarks"></a>Poznámky  
 V `Assembly` rámci manifestu lze definovat pouze jednu strukturu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

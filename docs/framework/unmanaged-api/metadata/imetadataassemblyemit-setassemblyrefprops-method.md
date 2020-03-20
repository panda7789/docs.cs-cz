---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176042"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
Upraví zadanou `AssemblyRef` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ar`  
 [v] Token metadat, který určuje `AssemblyRef` strukturu metadat, která má být změněna.  
  
 `pbPublicKeyOrToken`  
 [v] Veřejný klíč vydavatele odkazované sestavení.  
  
 `cbPublicKeyOrToken`  
 [v] Velikost v bajtů `pbPublicKeyOrToken`.  
  
 `szName`  
 [v] Text čitelný pro člověka název sestavení.  
  
 `pMetaData`  
 [v] Ukazatel na instanci ASSEMBLYMETADATA, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.  
  
 `pbHashValue`  
 [v] Ukazatel na data hash přidružená k sestavení.  
  
 `cbHashValue`  
 [v] Velikost v bajtů `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [v] Bitová kombinace hodnot [AssemblyRefFlags,](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) které určují atributy odkazovaného sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li `AssemblyRef` vytvořit strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

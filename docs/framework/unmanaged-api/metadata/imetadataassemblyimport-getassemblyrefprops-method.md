---
title: IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa633d554652050af51065e11221f898b34d5c63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772680"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
Získá sadu vlastností pro odkaz na sestavení s podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdar`  
 [in] `mdAssemblyRef` Token metadat, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.  
  
 `ppbPublicKeyOrToken`  
 [out] Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKeyOrToken`  
 [out] Počet bajtů vrácených veřejný klíč nebo token.  
  
 `szName`  
 [out] Jednoduchý název sestavení.  
  
 `cchName`  
 [in] Velikost v široké znaky z `szName`.  
  
 `pchName`  
 [out] Ukazatel na počet skutečně vrácených v široké znaky `szName`.  
  
 `pMetaData`  
 [out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.  
  
 `ppbHashValue`  
 [out] Ukazatel na hodnotu hash. Toto je hodnota hash pomocí algoritmu SHA-1 z `PublicKey` vlastnost sestavení odkazuje, není-li arfFullOriginator příznak [assemblyrefflags –](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) výčtu je nastavena.  
  
 `pcbHashValue`  
 [out] Počet široké znaky v hodnotě vrácené hodnoty hash.  
  
 `pdwAssemblyRefFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použité u sestavení. Hodnota příznaků je kombinace jedné nebo více [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu S_OK Pokud neproběhne úspěšně. v opačném případě vrátí jednu z kódy chyb, které jsou definovány v souboru hlaviček Winerror.h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

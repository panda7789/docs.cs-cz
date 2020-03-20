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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175964"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
Získá sadu vlastností pro odkaz na sestavení s zadaným podpisem metadat.  
  
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
 [v] Token `mdAssemblyRef` metadat, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.  
  
 `ppbPublicKeyOrToken`  
 [out] Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKeyOrToken`  
 [out] Počet bajtů ve vráceném veřejném klíči nebo tokenu.  
  
 `szName`  
 [out] Jednoduchý název sestavení.  
  
 `cchName`  
 [v] Velikost , v širokých `szName`znaků, .  
  
 `pchName`  
 [out] Ukazatel na počet širokých znaků skutečně `szName`vrácených v .  
  
 `pMetaData`  
 [out] Ukazatel na strukturu ASSEMBLYMETADATA, která obsahuje metadata sestavení.  
  
 `ppbHashValue`  
 [out] Ukazatel na hodnotu hash. Toto je algoritmus hash pomocí algoritmu `PublicKey` SHA-1 vlastnosti naváděného sestavení, pokud není nastaven příznak arfFullOriginator výčtu [AssemblyRefFlags.](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)  
  
 `pcbHashValue`  
 [out] Počet širokých znaků ve vrácené hodnotě hash.  
  
 `pdwAssemblyRefFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použitá v sestavení. Hodnota příznaků je kombinací jedné nebo více hodnot [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí S_OK pokud je úspěšná; v opačném případě vrátí jeden z kódů chyb definovaných v souboru hlavičky Winerror.h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

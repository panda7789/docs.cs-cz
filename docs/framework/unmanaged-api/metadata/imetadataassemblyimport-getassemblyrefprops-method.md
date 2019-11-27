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
ms.openlocfilehash: 4149db74adfa26df221eed5c590766a023bb105e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448223"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
Získá sadu vlastností pro odkaz na sestavení se zadaným podpisem metadat.  
  
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
 pro Token metadat `mdAssemblyRef`, který představuje odkaz na sestavení, pro který se mají získat vlastnosti.  
  
 `ppbPublicKeyOrToken`  
 mimo Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKeyOrToken`  
 mimo Počet bajtů v vráceném veřejném klíči nebo tokenu.  
  
 `szName`  
 mimo Jednoduchý název sestavení.  
  
 `cchName`  
 pro Velikost v rámci velkých znaků `szName`.  
  
 `pchName`  
 mimo Ukazatel na počet velkých znaků, který je ve skutečnosti vrácen v `szName`.  
  
 `pMetaData`  
 mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.  
  
 `ppbHashValue`  
 mimo Ukazatel na hodnotu hash. Toto je hodnota hash pomocí algoritmu SHA-1 vlastnosti `PublicKey` odkazovaného sestavení, pokud není nastaven příznak arfFullOriginator výčtu [AssemblyRefFlags –](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) .  
  
 `pcbHashValue`  
 mimo Počet velkých znaků v vrácené hodnotě hash.  
  
 `pdwAssemblyRefFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro sestavení. Hodnota příznaků je kombinací jedné nebo více hodnot [CorAssemblyFlags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí S_OK, pokud je úspěšná; v opačném případě vrátí jeden z kódů chyb definovaných v souboru hlaviček Winerror. h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

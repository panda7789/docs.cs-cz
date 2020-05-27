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
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009064"
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
 pro `mdAssemblyRef`Token metadat, který představuje odkaz na sestavení, pro který se mají získat vlastnosti.  
  
 `ppbPublicKeyOrToken`  
 mimo Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKeyOrToken`  
 mimo Počet bajtů v vráceném veřejném klíči nebo tokenu.  
  
 `szName`  
 mimo Jednoduchý název sestavení.  
  
 `cchName`  
 pro Velikost ve velkých znakech `szName` .  
  
 `pchName`  
 mimo Ukazatel na počet velkých znaků, které se ve skutečnosti vrátily `szName` .  
  
 `pMetaData`  
 mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.  
  
 `ppbHashValue`  
 mimo Ukazatel na hodnotu hash. Toto je hodnota hash pomocí algoritmu SHA-1 `PublicKey` Vlastnosti odkazovaného sestavení, pokud není nastaven příznak arfFullOriginator výčtu [AssemblyRefFlags –](assemblyrefflags-enumeration.md) .  
  
 `pcbHashValue`  
 mimo Počet velkých znaků v vrácené hodnotě hash.  
  
 `pdwAssemblyRefFlags`  
 mimo Ukazatel na příznaky, které popisují metadata použitá pro sestavení. Hodnota příznaků je kombinací jedné nebo více hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí S_OK, pokud je úspěšná; v opačném případě vrátí jeden z kódů chyb definovaných v souboru hlaviček Winerror. h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)

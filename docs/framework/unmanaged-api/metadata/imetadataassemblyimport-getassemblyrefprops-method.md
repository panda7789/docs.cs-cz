---
title: "IMetaDataAssemblyImport::GetAssemblyRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76ae1d81db314530ab33a42cb99824da1745dff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps – metoda
Získá sadu vlastností pro odkaz na sestavení s podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mdar`  
 [v] `mdAssemblyRef` Metadata token, který představuje odkaz na sestavení, pro které chcete získat vlastnosti.  
  
 `ppbPublicKeyOrToken`  
 [out] Ukazatel na veřejný klíč, nebo token pro metadata.  
  
 `pcbPublicKeyOrToken`  
 [out] Počet bajtů vrácených veřejný klíč, nebo token.  
  
 `szName`  
 [out] Jednoduchý název sestavení.  
  
 `cchName`  
 [v] Velikost v široké znaků, z `szName`.  
  
 `pchName`  
 [out] Ukazatel na počet široké znaků ve skutečnosti, vrátí se v `szName`.  
  
 `pMetaData`  
 [out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.  
  
 `ppbHashValue`  
 [out] Ukazatel na hodnotu hash. Toto je hodnota hash, pomocí algoritmu SHA-1 z `PublicKey` vlastnost sestavení odkazováno, pokud arfFullOriginator příznak [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) výčtu nastavena.  
  
 `pcbHashValue`  
 [out] Počet široké znaků v hodnotě vrácené hodnoty hash.  
  
 `pdwAssemblyRefFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použijí k sestavení. Hodnota příznaky je kombinací jednoho nebo více [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí S_OK Pokud neproběhne úspěšně. jinak vrátí jeden z definovaných v záhlaví souboru Winerror.h kódy chyb.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

---
title: IMetaDataAssemblyImport::GetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449439"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps – metoda
Získá sadu vlastností pro sestavení se zadaným podpisem metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mda`  
 [in]. Token metadat `mdAssembly`, který představuje sestavení, pro které mají být získány vlastnosti.  
  
 `ppbPublicKey`  
 mimo Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKey`  
 mimo Počet bajtů ve vráceném veřejném klíči.  
  
 `pulHashAlgId`  
 mimo Ukazatel na algoritmus použitý k hashování souborů v sestavení.  
  
 `szName`  
 mimo Jednoduchý název sestavení.  
  
 `cchName`  
 pro Velikost v rámci velkých znaků `szName`.  
  
 `pchName`  
 mimo Počet znaků, které jsou ve skutečnosti vraceny `szName`.  
  
 `pMetaData`  
 mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.  
  
 `pdwAssemblyFlags`  
 mimo Příznaky, které popisují metadata použitá pro sestavení. Tato hodnota je kombinací jedné nebo více hodnot [CorAssemblyFlags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

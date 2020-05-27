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
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009051"
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
 [in]. `mdAssembly`Token metadat představující sestavení, pro které mají být získány vlastnosti.  
  
 `ppbPublicKey`  
 mimo Ukazatel na veřejný klíč nebo token metadat.  
  
 `pcbPublicKey`  
 mimo Počet bajtů ve vráceném veřejném klíči.  
  
 `pulHashAlgId`  
 mimo Ukazatel na algoritmus použitý k hashování souborů v sestavení.  
  
 `szName`  
 mimo Jednoduchý název sestavení.  
  
 `cchName`  
 pro Velikost ve velkých znakech `szName` .  
  
 `pchName`  
 mimo Počet skutečně vrácených znaků `szName` .  
  
 `pMetaData`  
 mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.  
  
 `pdwAssemblyFlags`  
 mimo Příznaky, které popisují metadata použitá pro sestavení. Tato hodnota je kombinací jedné nebo více hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)

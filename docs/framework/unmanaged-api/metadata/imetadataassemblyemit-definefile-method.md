---
title: IMetaDataAssemblyEmit::DefineFile – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46fa6ab3ea4a63583b01ffe25d22840301613100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile – metoda
Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [v] Název souboru, který se má používat.  
  
 `pbHashValue`  
 [v] Ukazatel na hodnotu hash data přidružená k sestavení.  
  
 `cbHashValue`  
 [v] Velikost v bajtech `pbHashValue`.  
  
 `dwFileFlags`  
 [v] Bitové kombinace `FileFlags` hodnoty, které určují nastavení vlastností.  
  
 `pmdf`  
 [out] Ukazatel na vrácený `File` tokenu.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `File` strukturu metadat musí být definovaná pro každý soubor, který byl součástí toto sestavení v čase, který byl vytvořený toto sestavení, s výjimkou souboru, který obsahuje metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

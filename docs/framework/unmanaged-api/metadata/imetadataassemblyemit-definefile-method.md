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
ms.openlocfilehash: 5ede66a39de292cd259cb12742e7c6df4ab5814f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720493"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile – metoda
Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.  
  
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
 [in] Název souboru, který se má používat.  
  
 `pbHashValue`  
 [in] Ukazatel na hodnotu hash dat přidružené k sestavení.  
  
 `cbHashValue`  
 [in] Velikost v bajtech `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Bitová kombinace hodnot `FileFlags` hodnoty, které určují nastavení vlastností.  
  
 `pmdf`  
 [out] Ukazatel na vrácenou `File` token.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `File` struktury metadat musí být definované pro každý soubor, který byl součástí tohoto sestavení v době, toto sestavení bylo sestaveno, s výjimkou souboru, který obsahuje metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

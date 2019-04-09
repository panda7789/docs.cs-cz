---
title: IMetaDataAssemblyEmit::DefineAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b95a583aec87e3ba3e247d1ef800302b62657837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176004"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly – metoda
Vytvoří `Assembly` struktury obsahující metadata pro zadané sestavení a vrátí token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKey`  
 [in] Veřejný klíč, který identifikuje vydavatele sestavení nebo hodnota NULL, pokud sestavení není silně pojmenováno.  
  
 `cbPublicKey`  
 [in] Velikost v bajtech `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Identifikátor algoritmu hash určený k šifrování souborů v sestavení nebo hodnota NULL k určení algoritmus SHA-1.  
  
 `szName`  
 [in] Uživatelsky čitelná textová název sestavení. Tato hodnota nesmí překročit 1024 znaků.  
  
 `pMetaData`  
 [in] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.  
  
 `dwAssemblyFlags`  
 [in] Kombinace [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které popisují funkce sestavení.  
  
 `pmda`  
 [out] Ukazatel na token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Pouze jeden `Assembly` metadat struktury lze definovat v rámci manifestu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

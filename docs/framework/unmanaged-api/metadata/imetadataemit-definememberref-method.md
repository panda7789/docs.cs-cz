---
title: IMetaDataEmit::DefineMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 881c0b1f755e750efcc74ca61a60bbd97bc5dba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinememberref-method"></a>IMetaDataEmit::DefineMemberRef – metoda
Definuje odkaz na člena modulu mimo aktuální obor a získá token pro tuto referenční definice.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkImport`  
 [v] Token pro člena cílové třídy nebo rozhraní, pokud člen není globální; Pokud je člen globální, `mdModuleRef` tokenu pro tento druhý soubor.  
  
 `szName`  
 [v] Název člena cíl.  
  
 `pvSigBlob`  
 [v] Podpis cíl člena.  
  
 `cbSigBlob`  
 [v] Počet bajtů v `pvSigBlob`.  
  
 `pmr`  
 [out] `mdMemberRef` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

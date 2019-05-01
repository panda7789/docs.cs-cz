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
ms.openlocfilehash: d5d386b1d3f95e703cc5d9ad1353ea6b84b5b455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043213"
---
# <a name="imetadataemitdefinememberref-method"></a>IMetaDataEmit::DefineMemberRef – metoda
Definuje odkaz na člena modulu mimo aktuální obor a získá token pro tuto definici odkazu.  
  
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
  
## <a name="parameters"></a>Parametry  
 `tkImport`  
 [in] Token pro cílový člen třídy nebo rozhraní, pokud člen není globální; Pokud je globální, člen `mdModuleRef` token pro tento soubor.  
  
 `szName`  
 [in] Jméno člena cíl.  
  
 `pvSigBlob`  
 [in] Podpis cílové člena.  
  
 `cbSigBlob`  
 [in] Počet bajtů v `pvSigBlob`.  
  
 `pmr`  
 [out] `mdMemberRef` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

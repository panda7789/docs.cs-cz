---
title: IMetaDataImport::GetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177216"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA – metoda
Získá relativní virtuální adresu (RVA) a příznaky implementace metody nebo pole reprezentované zadaným tokenem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [v] A MethodDef nebo FieldDef token metadat, který představuje objekt kódu vrátit RVA pro. Pokud je token FieldDef, pole musí být globální proměnná.  
  
 `pulCodeRVA`  
 [out] Ukazatel na relativní virtuální adresu objektu kódu reprezentovaného tokenem.  
  
 `pdwImplFlags`  
 [out] Ukazatel na příznaky implementace pro metodu. Tato hodnota je bitová maska z [cormethodimpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu. Hodnota je `pdwImplFlags` platná pouze `tk` v případě, že je token MethodDef.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

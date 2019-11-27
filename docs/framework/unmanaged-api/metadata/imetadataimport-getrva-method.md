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
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436953"
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
 pro Token metadat MethodDef nebo FieldDef, který představuje objekt kódu, pro který má být vrácena adresa RVA. Pokud je tokenem FieldDef, musí být pole globální proměnná.  
  
 `pulCodeRVA`  
 mimo Ukazatel na relativní virtuální adresu objektu kódu reprezentovaného tokenem.  
  
 `pdwImplFlags`  
 mimo Ukazatel na příznaky implementace pro metodu. Tato hodnota je Bitová maska z výčtu [CorMethodImpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) . Hodnota `pdwImplFlags` je platná pouze v případě, že `tk` je token MethodDef.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

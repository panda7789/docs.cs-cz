---
title: IMetaDataEmit2::DefineMethodSpec – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503814"
---
# <a name="imetadataemit2definemethodspec-method"></a>IMetaDataEmit2::DefineMethodSpec – metoda
Vytvoří obecnou instanci metody a získá do definice token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkParent`  
 pro Token pro metodu, pro kterou chcete vytvořit obecnou instanci. Token musí být typu `mdMethodDef` nebo `mdMemberRef` .  
  
 `pvSigBlob`  
 pro Ukazatel na binární podpis modelu COM+ metody.  
  
 `cbSibBlob`  
 pro Velikost v bajtech `pvSigBlob` .  
  
 `pmi`  
 mimo Token definice podpisu metadat metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)

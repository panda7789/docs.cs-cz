---
title: IMetaDataImport2::GetMethodSpecProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490442"
---
# <a name="imetadataimport2getmethodspecprops-method"></a>IMetaDataImport2::GetMethodSpecProps – metoda
Získá podpis metadat metody, na kterou odkazuje zadaný token MethodSpec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a>Parametry  
 `mi`  
 pro Token MethodSpec, který představuje instanci metody.  
  
 `tkParent`  
 mimo Ukazatel na token MethodDef nebo MethodRef, který představuje definici metody.  
  
 `ppvSigBlob`  
 mimo Ukazatel na binární podpis metadat metody.  
  
 `pcbSigBlob`  
 mimo Velikost v bajtech `ppvSigBlob` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)

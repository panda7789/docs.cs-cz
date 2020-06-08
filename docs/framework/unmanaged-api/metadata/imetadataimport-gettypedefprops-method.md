---
title: IMetaDataImport::GetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490793"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps – metoda
Vrátí informace o metadatech <xref:System.Type> reprezentovaných zadaným tokenem typedef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro Token TypeDef, který představuje typ, pro který se mají vracet metadata.  
  
 `szTypeDef`  
 mimo Vyrovnávací paměť obsahující název typu.  
  
 `cchTypeDef`  
 pro Velikost v různých znacích `szTypeDef` .  
  
 `pchTypeDef`  
 mimo Počet znaků vrácených v rámci `szTypeDef` .  
  
 `pdwTypeDefFlags`  
 mimo Ukazatel na libovolný příznak, který upraví definici typu. Tato hodnota je Bitová maska z výčtu [CorTypeAttr –](cortypeattr-enumeration.md) .  
  
 `ptkExtends`  
 mimo Token metadat TypeDef nebo TypeRef, který představuje základní typ požadovaného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)

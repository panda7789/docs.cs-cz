---
title: IMetaDataImport2::GetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 7e97b2d4ad1fec4675d1484959b115a4d4b87e90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490611"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps – metoda
Získá metadata přidružená k obecnému parametru reprezentovanému zadaným tokenem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `gp`  
 pro Token, který představuje obecný parametr, pro který se mají vracet metadata  
  
 `pulParamSeq`  
 mimo Pořadové místo `Type` parametru v nadřazeném konstruktoru nebo metodě.  
  
 `pdwParamFlags`  
 mimo Hodnota výčtu [CorGenericParamAttr –](corgenericparamattr-enumeration.md) , která popisuje `Type` pro obecný parametr.  
  
 `ptOwner`  
 mimo Token TypeDef nebo MethodDef, který představuje vlastníka parametru.  
  
 `reserved`  
 mimo Vyhrazeno pro budoucí rozšíření.  
  
 `wzName`  
 mimo Název obecného parametru.  
  
 `cchName`  
 pro Velikost `wzName` vyrovnávací paměti.  
  
 `pchName`  
 mimo Vrácená velikost názvu, v rámci velkých znaků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)

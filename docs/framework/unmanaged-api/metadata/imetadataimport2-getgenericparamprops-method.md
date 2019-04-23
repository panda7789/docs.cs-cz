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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55a765fe3942cbf71a8460187e829dc7f3ca877e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082331"
---
# <a name="imetadataimport2getgenericparamprops-method"></a>IMetaDataImport2::GetGenericParamProps – metoda
Získá metadata přidružená k obecný parametr reprezentována zadaného tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Token, který představuje obecný parametr, pro které se mají vrátit metadata.  
  
 `pulParamSeq`  
 [out] Pořadové číslo pozice `Type` parametr v konstruktoru nadřazené nebo metody.  
  
 `pdwParamFlags`  
 [out] Hodnota [corgenericparamattr –](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje `Type` pro obecný parametr.  
  
 `ptOwner`  
 [out] Token TypeDef nebo MethodDef, který představuje vlastníka parametru.  
  
 `reserved`  
 [out] Vyhrazeno pro budoucí rozšíření.  
  
 `wzName`  
 [out] Název obecného parametru.  
  
 `cchName`  
 [in] Velikost `wzName` vyrovnávací paměti.  
  
 `pchName`  
 [out] Vrácená velikost názvu v širokých znaků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

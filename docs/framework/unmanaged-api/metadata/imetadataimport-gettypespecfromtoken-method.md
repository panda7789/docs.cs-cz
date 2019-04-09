---
title: IMetaDataImport::GetTypeSpecFromToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 362cbe9ff19e74bafc73fde857d231185179efbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079549"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a>IMetaDataImport::GetTypeSpecFromToken – metoda
Získá metadata binární podpis specifikace typu, který je reprezentován zadaného tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `typespec`  
 [in] Token TypeSpec tokenu přidružený k podpisu požadovaná metadata.  
  
 `ppvSig`  
 [out] Ukazatel na podpis binárního metadat.  
  
 `pcbSig`  
 [out] Velikost v bajtech, podpis metadat.  
  
## <a name="return-value"></a>Návratová hodnota  
 HRESULT, která indikuje úspěch nebo neúspěch. Chyby lze testovat pomocí – makro se nezdařilo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

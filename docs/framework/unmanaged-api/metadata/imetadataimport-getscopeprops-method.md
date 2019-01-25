---
title: IMetaDataImport::GetScopeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7c41e05ecf4e33f7ca711befdd90275452439df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718855"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps – metoda
Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [out] Vyrovnávací paměť pro název sestavení nebo modulu.  
  
 `cchName`  
 [in] Velikost v širokých znaků `szName`.  
  
 `pchName`  
 [out] Počet širokých znaků, které jsou vráceny v `szName`.  
  
 `pmvid`  
 [out, volitelné] Ukazatel na identifikátor GUID, který jednoznačně identifikuje verzi sestavení nebo modulu.  
  
## <a name="remarks"></a>Poznámky  
 [Imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda se používá k nastavení těchto vlastností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: IMetaDataConverter::GetTypeLibFromMetaData – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ab1d39ddb53e08e6fd36016f544162e2b11edb0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472067"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>IMetaDataConverter::GetTypeLibFromMetaData – metoda
Získá ukazatel `ITypeLib` instanci, která představuje knihovnu typů, který má zadané názvy knihovny a modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `strModule`  
 [in] Název knihovny typů modulu.  
  
 `strTlbName`  
 [in] Název knihovny typů.  
  
 `ppITL`  
 [out] Ukazatel na umístění, která bude přijímat adresy `ITypeLib` instanci, která představuje knihovnu typů.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataConverter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)

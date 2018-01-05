---
title: "GetPublicKeyToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken – metoda
Načte token veřejného klíče pro danou keyfile nebo kontejneru klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszKeyFile`  
 Název souboru klíče.  
  
 `pszKeyContainer`  
 Název kontejneru klíčů.  
  
 `pvPublicKeyToken`  
 Adresa, kde má být uložena token veřejného klíče.  
  
 `pcbPublicKeyToken`  
 Určuje velikost v bajtech vyrovnávací paměti indikován `pvPublicKeyToken`. Po návratu obsahuje skutečný počet bajtů použitých.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

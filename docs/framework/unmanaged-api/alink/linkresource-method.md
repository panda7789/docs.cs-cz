---
title: "LinkResource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a>LinkResource – metoda
Odkazy v prostředku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
 `pszFileName`  
 Název souboru.  
  
 `pszNewLocation`  
 Volitelné nový název souboru. Pokud není hodnotou NULL, `pszFileName` bude zkopírován do pszNewLocation.  
  
 `pszResourceName`  
 Název prostředku.  
  
 `dwFlags`  
 Usnadnění flags – například `mrPublic` a `mrPrivate`. Tento parametr může být předán [DefineManifestResource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [Ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

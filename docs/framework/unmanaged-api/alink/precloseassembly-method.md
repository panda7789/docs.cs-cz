---
title: "PreCloseAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a4d1f2eed036552ab17b6768b7b2d84f4a52c9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="precloseassembly-method"></a>PreCloseAssembly – metoda
Zavře souboru sestavení. Volejte tuto metodu po zavření všechny ostatní soubory, ale před jeho zavřením souboru sestavení. Nevolejte tuto metodu pro nevázaný moduly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

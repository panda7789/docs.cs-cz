---
title: "EndMerge – metoda"
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
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a>EndMerge – metoda
Označuje, že byly všechny vlastní atributy sloučeny do oboru vysílat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

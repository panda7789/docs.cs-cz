---
title: "SetNonAssemblyFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetNonAssemblyFlags
api_location: alink.dll
api_type: COM
f1_keywords: SetNonAssemblyFlags
helpviewer_keywords: SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5f8761259e89b4befd0eeaf893ffbe5d4142350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setnonassemblyflags-method"></a>SetNonAssemblyFlags – metoda
Nastaví příznaky, které nejsou specifické pro sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `afFlags`  
 Příznaky ALink.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také  
 [Ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

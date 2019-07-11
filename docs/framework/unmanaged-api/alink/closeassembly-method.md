---
title: CloseAssembly – metoda
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e0b7b3547bb246588f6b255483d4c317e0df88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742226"
---
# <a name="closeassembly-method"></a>CloseAssembly – metoda
Dokončí operace sestavení. Tuto metodu volejte před zahájením nové sestavení nebo nevázaného modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)

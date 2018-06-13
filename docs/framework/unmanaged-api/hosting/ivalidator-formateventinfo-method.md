---
title: IValidator::FormatEventInfo – metoda
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 875052ed26e83de50807e33e9c74dcf89f7ee679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440642"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo – metoda
Získá chybovou zprávu odpovídající zadané chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hVECode`  
 [v] Hodnota HRESULT, který byl předán na obslužnou rutinu chyby ověření.  
  
 `Context`  
 [v] A `VEContext` instanci, která obsahuje kontextové informace o chybě ověření.  
  
 `msg`  
 [ve out] Řetězec, který obsahuje vrácené chybovou zprávu.  
  
 `ulMaxLength`  
 [v] Maximální délka chybové zprávy.  
  
 `psa`  
 [v] Bezpečné pole, které obsahuje další parametry popisující chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 

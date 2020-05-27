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
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008570"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo – metoda
Načte chybovou zprávu odpovídající zadané chybě ověřování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hVECode`  
 pro Hodnota HRESULT, která byla předána obslužné rutině chyby ověřování.  
  
 `Context`  
 pro `VEContext`Instance obsahující kontextové informace o chybě ověření.  
  
 `msg`  
 [in, out] Řetězec, který obsahuje vrácenou chybovou zprávu.  
  
 `ulMaxLength`  
 pro Maximální délka chybové zprávy.  
  
 `psa`  
 pro Bezpečné pole, které obsahuje další parametry popisující chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  

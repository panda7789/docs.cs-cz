---
title: ICeeGen::GetSectionBlock – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008316"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock – metoda
Získá blok oddílu základu kódu.  
  
 Tato metoda je zastaralá a neměla by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>Parametry  
 `section`  
 pro Oddíl, ze kterého má být načten blok základního kódu.  
  
 `len`  
 pro Délka bloku, který má být načten.  
  
 `align`  
 pro Bajt relativní ke začátku oddílu, s nímž má být zarovnaný první bajt bloku. Toto je pozice bloku v rámci oddílu.  
  
 `ppBytes`  
 mimo Ukazatel na umístění, které přijímá adresu načteného bloku.  
  
## <a name="remarks"></a>Poznámky  
 Volejte `GetSectionBlock` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICeeGen – rozhraní](iceegen-interface.md)

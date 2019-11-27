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
ms.openlocfilehash: 0731053fb37c775d25052a5fd99a479a44ff5862
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434876"
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
 Vyvolejte `GetSectionBlock` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176081"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock – metoda
Získá blok oddílu základu kódu.  
  
 Tato metoda je zastaralá a neměla by být použita.  
  
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
 [v] Oddíl, ze kterého chcete načíst blok základu kódu.  
  
 `len`  
 [v] Délka bloku, který má být načten.  
  
 `align`  
 [v] Bajt, vzhledem k začátku oddílu, se kterým chcete zarovnat první bajt bloku. Toto je pozice bloku v sekci.  
  
 `ppBytes`  
 [out] Ukazatel na umístění, které přijímá adresu načteného bloku.  
  
## <a name="remarks"></a>Poznámky  
 Volání `GetSectionBlock` pouze v případě, že máte zvláštní požadavky oddílu, které nejsou zpracovány jinými metodami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

---
title: StrongNameHashSize – funkce
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: c656f73748faf8be7124be65f3ed455f2d5fd07a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105192"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize – funkce
Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameHashSize –](../hosting/iclrstrongname-strongnamehashsize-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ulHashAlg`  
 pro Algoritmus hash používaný k výpočtu velikosti vyrovnávací paměti.  
  
 `pcbSize`  
 mimo Vrácená velikost vyrovnávací paměti (v bajtech).  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se funkce `StrongNameHashSize` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameHashSize – metoda](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

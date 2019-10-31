---
title: StrongNameSignatureVerificationEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121149"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx – funkce
Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureVerificationEx –](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenositelnému spustitelnému souboru (. exe nebo. dll) pro sestavení, které má být ověřeno.  
  
 `fForceVerification`  
 [in] `true` provádět ověřování, i když je nutné přepsat nastavení registru. v opačném případě `false`.  
  
 `pfWasVerified`  
 [out] `true`, jestli se podpis silného názvu ověřil; v opačném případě `false`. `pfWasVerified` je také nastaveno na `false`, pokud bylo ověření úspěšné z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, zda bylo ověření úspěšné; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 `StrongNameSignatureVerificationEx` poskytuje možnost podobnou funkci [StrongNameSignatureVerification –](strongnamesignatureverification-function.md) . Druhý vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` jsou však typu `BOOLEAN` namísto `DWORD`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerificationEx – metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification – metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

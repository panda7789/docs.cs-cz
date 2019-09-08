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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798913"
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
 pro provést ověření, i když je nutné přepsat nastavení registru, `false`jinak. `true`  
  
 `pfWasVerified`  
 mimo Pokud byl podpis silného názvu ověřen; `false`v opačném případě. `true` `pfWasVerified`je také nastaveno na `false` , pokud bylo ověření úspěšné z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud bylo ověření úspěšné; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 `StrongNameSignatureVerificationEx`poskytuje funkci podobnou funkci [StrongNameSignatureVerification –](strongnamesignatureverification-function.md) . Druhý vstupní parametr a výstupní parametr pro `StrongNameSignatureVerificationEx` jsou však typu `BOOLEAN` místo `DWORD`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerificationEx – metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification – metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

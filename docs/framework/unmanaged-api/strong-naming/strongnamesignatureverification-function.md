---
title: StrongNameSignatureVerification – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129236"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification – funkce
Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureVerification –](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenositelnému spustitelnému souboru (. dll nebo. exe) pro sestavení, které se má ověřit  
  
 `dwInFlags`  
 pro Příznaky pro změnu chování ověřování. Podporovány jsou následující hodnoty:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) – vynutí ověření i v případě, že je nutné přepsat nastavení registru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) – určuje, že se jedná o první ověření manifestu.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) – určuje, že mezipaměť bude umožňovat přístup pouze uživatelům, kteří mají oprávnění správce.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) – určuje, zda bude sestavení přístupné pouze pro aktuálního uživatele.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) – určuje, že mezipaměť nebude poskytovat žádné záruky omezení přístupu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) – vyhrazeno pro interní ladění.  
  
 `pdwOutFlags`  
 mimo Příznaky označující, zda byl ověřen podpis silného názvu. Je podporována následující hodnota:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) – Tato hodnota je nastavena na hodnotu `false` a určí, že ověření proběhlo úspěšně z důvodu nastavení registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, zda bylo ověření úspěšné; v opačném případě `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureVerification – metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx – metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

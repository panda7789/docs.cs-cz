---
title: StrongNameKeyGen – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 79b2235e3645c89c2cd9ebcce079d5eb7efdd162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128743"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen – funkce
Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGen –](../hosting/iclrstrongname-strongnamekeygen-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 pro Požadovaný název kontejneru klíčů. `wszKeyContainer` musí být neprázdný řetězec nebo hodnota null, aby se vygeneroval dočasný název.  
  
 `dwFlags`  
 pro Určuje, jestli se má zaregistrovaný klíč ponechat. Podporovány jsou následující hodnoty:  
  
- 0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.  
  
- 0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.  
  
 `ppbKeyBlob`  
 mimo Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 mimo Velikost `ppbKeyBlob`v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `StrongNameKeyGen` vytvoří 1024 bitový klíč. Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.  
  
 Pokud se funkce `StrongNameKeyGen` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameKeyGen – metoda](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx – metoda](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

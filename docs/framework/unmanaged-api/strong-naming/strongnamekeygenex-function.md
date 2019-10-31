---
title: StrongNameKeyGenEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125218"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx – funkce
Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silného názvu.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGenEx –](../hosting/iclrstrongname-strongnamekeygenex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
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
  
 `dwKeySize`  
 pro Požadovaná velikost klíče v bitech.  
  
 `ppbKeyBlob`  
 mimo Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 mimo Velikost `ppbKeyBlob`v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 .NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` 1024 bitů pro podepsání sestavení silným názvem; verze 2,0 přidává podporu pro 2048 bitové klávesy.  
  
 Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.  
  
 Pokud se funkce `StrongNameKeyGenEx` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameKeyGenEx – metoda](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen – metoda](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

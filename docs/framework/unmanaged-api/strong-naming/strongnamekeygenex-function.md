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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9ab908866402bd7a883114466f32921321a5ee6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799009"
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
 pro Požadovaný název kontejneru klíčů. `wszKeyContainer`aby bylo možné vytvořit dočasný název, musí být neprázdný řetězec nebo hodnota null.  
  
 `dwFlags`  
 pro Určuje, jestli se má zaregistrovaný klíč ponechat. Podporovány jsou následující hodnoty:  
  
- 0x00000000 – používá se `wszKeyContainer` , pokud je null k vygenerování dočasného názvu kontejneru klíčů.  
  
- 0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.  
  
 `dwKeySize`  
 pro Požadovaná velikost klíče v bitech.  
  
 `ppbKeyBlob`  
 mimo Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 mimo Velikost v bajtech `ppbKeyBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 .NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` pro podepsání sestavení silným názvem 1024 bitů. verze 2,0 přidá podporu 2048 pro 64bitové klíče.  
  
 Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.  
  
 Pokud se `StrongNameKeyGenEx` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameKeyGenEx – metoda](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen – metoda](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

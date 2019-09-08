---
title: StrongNameGetPublicKey – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799056"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey – funkce
Získá veřejný klíč z páru privátních a veřejných klíčů. Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameGetPublicKey –](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče. Pokud `pbKeyBlob` má hodnotu null `szKeyContainer` , musí v rámci CSP určovat platný kontejner. V tomto případě `StrongNameGetPublicKey` extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.  
  
 Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys. V tuto chvíli není podporovaný žádný jiný typ klíčů.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` . Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `szKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 mimo Vrácený objekt BLOB veřejného klíče. `ppbPublicKeyBlob` Parametr je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu. Volající musí uvolnit paměť pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .  
  
 `pcbPublicKeyBlob`  
 mimo Velikost vráceného objektu BLOB veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](publickeyblob-structure.md) .  
  
 Pokud se `StrongNameGetPublicKey` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameGetPublicKey – metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey – metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob – struktura](publickeyblob-structure.md)

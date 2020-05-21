---
title: ICLRStrongName::StrongNameGetPublicKey – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763124"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey – metoda
Získá veřejný klíč z páru veřejného a privátního klíče. Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče. Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musí v rámci CSP určovat platný kontejner. V tomto případě metoda [ICLRStrongName:: StrongNameGetPublicKey –](iclrstrongname-strongnamegetpublickey-method.md) extrahuje veřejný klíč z páru klíčů uloženého v kontejneru.  
  
 Pokud hodnota `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys. V tuto chvíli není podporovaný žádný jiný typ klíčů.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob` .  
  
 `ppbPublicKeyBlob`  
 mimo Vrácený objekt BLOB veřejného klíče. `ppbPublicKeyBlob`Parametr je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu. Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbPublicKeyBlob`  
 mimo Velikost vráceného objektu BLOB veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromPublicKey – metoda](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob – struktura](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)

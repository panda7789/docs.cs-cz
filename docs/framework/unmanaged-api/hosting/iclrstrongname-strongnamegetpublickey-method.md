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
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181940"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey – metoda
Získá veřejný klíč z dvojice veřejného a soukromého klíče. Pár klíčů lze dodat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP) nebo jako nezpracovaná kolekce bajtů.  
  
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
 [v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče. Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci ověřovatce. V tomto případě [metoda ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrahuje veřejný klíč z dvojice klíčů uložených v kontejneru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).  
  
 Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA). V současné době nejsou podporovány žádné jiné typy klíčů.  
  
 `pbKeyBlob`  
 [v] Ukazatel na dvojici veřejného a soukromého klíče. Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` je null, předpokládá `szKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtů `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Vrácený veřejný klíč BLOB. Parametr `ppbPublicKeyBlob` je přidělen a běžný jazyk runtime a vrácena volajícímu. Volající musí uvolnit paměť pomocí metody [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbPublicKeyBlob`  
 [out] Velikost vráceného objektu BLOB veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

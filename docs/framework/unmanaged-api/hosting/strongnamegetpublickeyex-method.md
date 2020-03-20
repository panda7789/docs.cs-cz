---
title: StrongNameGetPublicKeyEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176224"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx – metoda
Získá veřejný klíč z dvojice veřejného a soukromého klíče a určuje algoritmus hash a algoritmus podpisu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzKeyContainer`  
 [v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče. Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě `StrongNameGetPublicKeyEx` metoda extrahuje veřejný klíč z dvojice klíčů uložené v kontejneru.  
  
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
  
 `uHashAlgId`  
 [v] Algoritmus hash sestavení. Seznam přijatých hodnot naleznete v části Poznámky.  
  
 `uReserved`  
 [v] Vyhrazeno pro budoucí použití; výchozí hodnota null.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce je uvedena sada `uHashAlgId` přijatých hodnot pro parametr.  
  
|Name (Název)|Hodnota|  
|----------|-----------|  
|Žádný|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|ŠA-384|0x800d|  
|ŠA-512|0x800e|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob – struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)

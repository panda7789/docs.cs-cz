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
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006369"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx – metoda
Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.  
  
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
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče. Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě `StrongNameGetPublicKeyEx` Metoda extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.  
  
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
  
 `uHashAlgId`  
 pro Algoritmus hash sestavení. Seznam přijatelných hodnot naleznete v části poznámky.  
  
 `uReserved`  
 pro Vyhrazeno pro budoucí použití; Výchozí hodnota je null.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) .  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka ukazuje sadu přijatelných hodnot `uHashAlgId` parametru.  
  
|Name|Hodnota|  
|----------|-----------|  
|Žádné|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromPublicKey – metoda](iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob – struktura](../strong-naming/publickeyblob-structure.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)
- [StrongNameGetPublicKey – metoda](iclrstrongname-strongnamegetpublickey-method.md)

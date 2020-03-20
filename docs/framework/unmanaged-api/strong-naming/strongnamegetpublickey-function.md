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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176926"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey – funkce
Získá veřejný klíč z dvojice soukromého a veřejného klíče. Pár klíčů lze dodat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP) nebo jako nezpracovaná kolekce bajtů.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::StrongNameGetPublicKey.](../hosting/iclrstrongname-strongnamegetpublickey-method.md)  
  
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
 [v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče. Pokud `pbKeyBlob` je `szKeyContainer` null, musí zadat platný kontejner v rámci ověřovatce. V tomto `StrongNameGetPublicKey` případě extrahuje veřejný klíč z dvojice klíčů uložené v kontejneru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).  
  
 Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA). V současné době nejsou podporovány žádné jiné typy klíčů.  
  
 `pbKeyBlob`  
 [v] Ukazatel na dvojici veřejného a soukromého klíče. Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` je null, předpokládá `szKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtů `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Vrácený veřejný klíč BLOB. Parametr `ppbPublicKeyBlob` je přidělen a běžný jazyk runtime a vrácena volajícímu. Volající musí uvolnit paměť pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbPublicKeyBlob`  
 [out] Velikost vráceného objektu BLOB veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`po úspěšném dokončení; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Veřejný klíč je obsažen ve struktuře [PublicKeyBlob.](publickeyblob-structure.md)  
  
 Pokud `StrongNameGetPublicKey` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameGetPublicKey – metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey – metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob – struktura](publickeyblob-structure.md)

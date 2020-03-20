---
title: ICLRStrongName::StrongNameSignatureGeneration – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178043"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration – metoda
Generuje podpis silného názvu pro zadané sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k souboru, který obsahuje manifest sestavení, pro které bude generován podpis silného názvu.  
  
 `wszKeyContainer`  
 [v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.  
  
 Pokud `pbKeyBlob` je `wszKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě dvojice klíčů uložená v kontejneru se používá k podepsání souboru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).  
  
 Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA). V současné době nejsou podporovány žádné jiné typy klíčů.  
  
 `pbKeyBlob`  
 [v] Ukazatel na dvojici veřejného a soukromého klíče. Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` je null, předpokládá `wszKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtů `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ukazatel na umístění, do kterého běžný jazyk runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, runtime ukládá podpis v `wszFilePath`souboru určeném .  
  
 Pokud `ppbSignatureBlob` není null, běžný jazyk common time přiděluje místo, ve kterém chcete vrátit podpis. Volající musí uvolnit toto místo pomocí [metody ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbSignatureBlob`  
 [out] Velikost vráceného podpisu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Zadejte `wszFilePath` hodnotu null pro výpočet velikosti podpisu bez vytvoření podpisu.  
  
 Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

---
title: ICLRStrongName::StrongNameSignatureGenerationEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 3ca11cfe948a53292de8e68d87e3e45816a18162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134999"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx – metoda
Vygeneruje podpis silného názvu pro zadané sestavení podle zadaných příznaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.  
  
 `wszKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud má `pbKeyBlob` hodnotu null, musí `wszKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`. Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost `pbKeyBlob`v bajtech.  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud je `ppbSignatureBlob` null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
 `dwFlags`  
 pro Jedna nebo více z následujících hodnot:  
  
- `SN_SIGN_ALL_FILES` (0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.  
  
- `SN_TEST_SIGN` (0x00000002) – otestuje podpis sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` pro výpočet velikosti podpisu bez vytvoření podpisu.  
  
 Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud je zadána `SN_SIGN_ALL_FILES`, ale není k dispozici veřejný klíč (`pbKeyBlob` i `wszFilePath` mají hodnotu null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.  
  
 Je-li zadán `SN_TEST_SIGN`, není záhlaví modulu CLR (Common Language Runtime) upraveno, aby označovalo, že sestavení je podepsáno silným názvem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

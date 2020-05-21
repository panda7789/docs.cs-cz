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
ms.openlocfilehash: 3529eceb179cc4b08d39f83d97d001a16e716918
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763056"
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
  
 Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud hodnota `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob` .  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath` .  
  
 Pokud hodnota `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
 `dwFlags`  
 pro Jedna nebo více z následujících hodnot:  
  
- `SN_SIGN_ALL_FILES`(0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.  
  
- `SN_TEST_SIGN`(0x00000002) – otestuje podpis sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 `wszFilePath`Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.  
  
 Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud `SN_SIGN_ALL_FILES` je zadána, ale veřejný klíč není zahrnut ( `pbKeyBlob` a `wszFilePath` jsou null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.  
  
 Pokud `SN_TEST_SIGN` je zadána, hlavička společného jazykového modulu runtime není upravena, aby označovala, že je sestavení podepsáno silným názvem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameSignatureGeneration – metoda](iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName – rozhraní](iclrstrongname-interface.md)

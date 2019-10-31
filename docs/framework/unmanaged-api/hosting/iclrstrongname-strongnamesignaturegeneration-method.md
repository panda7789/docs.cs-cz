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
ms.openlocfilehash: 8013d805716bbe6407eeed664966fe667282188a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135012"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration – metoda
Vygeneruje podpis silného názvu pro zadané sestavení.  
  
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
 pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.  
  
 `wszKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud má `pbKeyBlob` hodnotu null, musí `wszKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys. V tuto chvíli není podporovaný žádný jiný typ klíčů.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`. Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost `pbKeyBlob`v bajtech.  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud je `ppbSignatureBlob` null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` pro výpočet velikosti podpisu bez vytvoření podpisu.  
  
 Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

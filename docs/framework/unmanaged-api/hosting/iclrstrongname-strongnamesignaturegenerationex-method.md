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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f1eb4236bab72caf4421342e1f54d6d2f32607
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207413"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx – metoda
Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.  
  
 `wszKeyContainer`  
 [in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.  
  
 Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).  
  
 `pbKeyBlob`  
 [in] Ukazatel na pár veřejného a privátního klíče. Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce. Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.  
  
 `cbKeyBlob`  
 [in] Velikost v bajtech, z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis. Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení. Volající musí uvolnit prostor pomocí [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.  
  
 `pcbSignatureBlob`  
 [out] Velikost v bajtech, vrácený podpis.  
  
 `dwFlags`  
 [in] Jeden nebo více z následujících hodnot:  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - přepočítá všechny hodnoty hash pro propojený moduly.  
  
-   `SN_TEST_SIGN` (0x00000002) - podpis testovacího sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.  
  
 Podpis může být buď uloženy přímo v souboru nebo vrátit zpět volajícímu.  
  
 Pokud `SN_SIGN_ALL_FILES` je zadán, ale není součástí veřejného klíče (obojí `pbKeyBlob` a `wszFilePath` má hodnotu Null), jsou přepočítány hodnoty hash propojených modulů, ale není znovu podepsat sestavení.  
  
 Pokud `SN_TEST_SIGN` je zadat hlavičce modulu CLR se nezmění k označení, že je sestavení podepsáno pomocí silného názvu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

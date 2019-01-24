---
title: StrongNameSignatureGenerationEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60825cb82097e6ec9c202efebe04a50b0f5a3771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508609"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx – funkce
Podpis silného názvu generuje pro zadané sestavení podle zadané příznaky.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamesignaturegenerationex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
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
  
 Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení. Volající musí uvolnit prostor pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.  
  
 `pcbSignatureBlob`  
 [out] Velikost v bajtech, vrácený podpis.  
  
 `dwFlags`  
 [in] Jeden nebo více z následujících hodnot:  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - přepočítá všechny hodnoty hash pro propojený moduly.  
  
-   `SN_TEST_SIGN` (0x00000002) - podpis testovacího sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.  
  
 Podpis může být buď uloženy přímo v souboru nebo vrátit zpět volajícímu.  
  
 Pokud `SN_SIGN_ALL_FILES` je zadán, ale není součástí veřejného klíče (obojí `pbKeyBlob` a `wszFilePath` má hodnotu Null), jsou přepočítány hodnoty hash propojených modulů, ale není znovu podepsat sestavení.  
  
 Pokud `SN_TEST_SIGN` je zadat hlavičce modulu CLR se nezmění k označení, že je sestavení podepsáno pomocí silného názvu.  
  
 Pokud `StrongNameSignatureGenerationEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

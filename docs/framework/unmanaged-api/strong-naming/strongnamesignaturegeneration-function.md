---
title: StrongNameSignatureGeneration – funkce
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55ff59d698a1ced689e23d9908ce6e273d8a9c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494542"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration – funkce
Podpis silného názvu generuje pro zadané sestavení.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
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
 [in] Cesta k souboru, který obsahuje manifest sestavení, pro který se vygeneruje podpis silného názvu.  
  
 `wszKeyContainer`  
 [in] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V takovém případě uložený v kontejneru pár klíčů se používá k podepsání souboru.  
  
 Pokud `pbKeyBlob` nemá hodnotu null, pár klíčů se předpokládá, že mají být obsažena v klíče binární velkých objektů (BLOB).  
  
 Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů. Jiné typy klíčů jsou v tuto chvíli nepodporuje.  
  
 `pbKeyBlob`  
 [in] Ukazatel na pár veřejného a privátního klíče. Tento pár je ve formátu vytvořené Win32 `CryptExportKey` funkce. Pokud `pbKeyBlob` je null, použije kontejneru klíčů určeném parametrem `wszKeyContainer` se předpokládá, že obsahuje pár klíčů.  
  
 `cbKeyBlob`  
 [in] Velikost v bajtech, z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ukazatel na umístění, do kterého modul common language runtime vrací podpis. Pokud `ppbSignatureBlob` je null, podpis modul runtime ukládá do souboru určeného `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` je nenulová, modul common language runtime přiděluje místo ke signatura vrácení. Volající musí uvolnit prostor pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.  
  
 `pcbSignatureBlob`  
 [out] Velikost v bajtech, vrácený podpis.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.  
  
 Podpis může být buď přímo v souboru uložit nebo vrátit zpět volajícímu.  
  
 Pokud `StrongNameSignatureGeneration` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

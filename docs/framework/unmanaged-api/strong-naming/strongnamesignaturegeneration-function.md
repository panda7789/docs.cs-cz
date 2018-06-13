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
ms.openlocfilehash: c0555299779aebc6cc37c3863e8b5504b357b262
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461490"
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
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [v] Cesta k souboru, který obsahuje manifest sestavení, pro které se budou generovat podpis silného názvu.  
  
 `wszKeyContainer`  
 [v] Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud `pbKeyBlob` má hodnotu null, `wszKeyContainer` musíte zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). Pár klíčů, ukládat do kontejneru v takovém případě se používá k podepsání souboru.  
  
 Pokud `pbKeyBlob` nemá hodnotu null, dvojici klíčů se předpokládá, že mají být obsažena v klíče binární rozsáhlý objekt (binární rozsáhlý OBJEKT).  
  
 Klíče musí být Rivest-Shamir-Adleman 1024 bitů (RSA) podpisových klíčů. Žádné jiné typy klíčů jsou podporovány v tuto chvíli.  
  
 `pbKeyBlob`  
 [v] Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořené Win32 `CryptExportKey` funkce. Pokud `pbKeyBlob` je null, kontejner klíčů určeného `wszKeyContainer` se předpokládá, že obsahovat dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtech z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ukazatel na umístění, do které modul common language runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, podpis modulu runtime ukládá do souboru určeného `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` je hodnotou not null, modul common language runtime přiděluje místo k vrácení podpis. Volající musí volné toto místo pomocí [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce.  
  
 `pcbSignatureBlob`  
 [out] Velikost v bajtech vrácený podpis.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` vypočítat velikost podpisu bez vytvoření podpisu.  
  
 Podpis může být uložená buď přímo v souboru nebo vrácen volajícímu.  
  
 Pokud `StrongNameSignatureGeneration` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameSignatureGeneration – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [StrongNameSignatureGenerationEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

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
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798977"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration – funkce
Vygeneruje podpis silného názvu pro zadané sestavení.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureGeneration –](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.  
  
 `wszKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud `pbKeyBlob` má hodnotu null `wszKeyContainer` , musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys. V tuto chvíli není podporovaný žádný jiný typ klíčů.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` . Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `wszKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` hodnota není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 `wszFilePath` Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.  
  
 Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud se `StrongNameSignatureGeneration` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureGeneration – metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx – metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

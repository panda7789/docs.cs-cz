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
ms.openlocfilehash: 9ab6fcb64e4654302e411d4dcc587df2e0bf1dc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125182"
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
  
 Pokud má `pbKeyBlob` hodnotu null, musí `wszKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys. V tuto chvíli není podporovaný žádný jiný typ klíčů.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`. Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `wszKeyContainer` obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost `pbKeyBlob`v bajtech.  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud je `ppbSignatureBlob` null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Zadejte hodnotu null pro `wszFilePath` pro výpočet velikosti podpisu bez vytvoření podpisu.  
  
 Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud se funkce `StrongNameSignatureGeneration` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureGeneration – metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx – metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

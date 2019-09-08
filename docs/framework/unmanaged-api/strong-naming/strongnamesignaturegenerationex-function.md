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
ms.openlocfilehash: 89398c221dcf9d6f89027f15da4062bc7ed67e3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798980"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx – funkce
Vygeneruje podpis silného názvu pro zadané sestavení podle zadaných příznaků.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameSignatureGenerationEx –](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k souboru, který obsahuje manifest sestavení, pro který bude vytvořen podpis silného názvu.  
  
 `wszKeyContainer`  
 pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.  
  
 Pokud `pbKeyBlob` má hodnotu null `wszKeyContainer` , musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě se k podepsání souboru používá pár klíčů uložený v kontejneru.  
  
 Pokud `pbKeyBlob` hodnota není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.  
  
 `pbKeyBlob`  
 pro Ukazatel na pár veřejného a privátního klíče. Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey` . Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že `wszKeyContainer` kontejner klíčů určený parametrem obsahuje dvojici klíčů.  
  
 `cbKeyBlob`  
 pro Velikost v bajtech `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 mimo Ukazatel na umístění, do kterého modul common language runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, modul runtime uloží podpis do souboru určeného parametrem `wszFilePath`.  
  
 Pokud `ppbSignatureBlob` hodnota není null, modul CLR (Common Language Runtime) přidělí místo, ve kterém se podpis vrátí. Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .  
  
 `pcbSignatureBlob`  
 mimo Velikost vráceného podpisu v bajtech.  
  
 `dwFlags`  
 pro Jedna nebo více z následujících hodnot:  
  
- `SN_SIGN_ALL_FILES`(0x00000001) – přepočítá všechny hodnoty hash pro propojené moduly.  
  
- `SN_TEST_SIGN`(0x00000002) – otestuje podpis sestavení.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="remarks"></a>Poznámky  
 `wszFilePath` Chcete-li vypočítat velikost podpisu bez vytvoření podpisu, zadejte hodnotu null.  
  
 Podpis může být buď uložen přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud `SN_SIGN_ALL_FILES` je zadána, ale veřejný klíč není zahrnut `pbKeyBlob` (a `wszFilePath` jsou null), jsou přepočítány hodnoty hash pro propojené moduly, ale sestavení není znovu podepsáno.  
  
 Pokud `SN_TEST_SIGN` je zadána, hlavička společného jazykového modulu runtime není upravena, aby označovala, že je sestavení podepsáno silným názvem.  
  
 Pokud se `StrongNameSignatureGenerationEx` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameSignatureGenerationEx – metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration – metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

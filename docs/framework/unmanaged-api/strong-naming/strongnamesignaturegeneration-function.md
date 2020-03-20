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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176900"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration – funkce
Generuje podpis silného názvu pro zadané sestavení.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::StrongNameSignatureGeneration.](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
  
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
 [v] Cesta k souboru, který obsahuje manifest sestavení, pro které bude generován podpis silného názvu.  
  
 `wszKeyContainer`  
 [v] Název kontejneru klíčů, který obsahuje dvojici veřejného a soukromého klíče.  
  
 Pokud `pbKeyBlob` je `wszKeyContainer` null, musí zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP). V tomto případě dvojice klíčů uložená v kontejneru se používá k podepsání souboru.  
  
 Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů je obsažena v binárním velkém objektu klíče (BLOB).  
  
 Klíče musí být 1024bitové podpisové klíče Rivest-Shamir-Adleman (RSA). V současné době nejsou podporovány žádné jiné typy klíčů.  
  
 `pbKeyBlob`  
 [v] Ukazatel na dvojici veřejného a soukromého klíče. Tento pár je ve formátu vytvořeném `CryptExportKey` funkcí Win32. Pokud `pbKeyBlob` je null, předpokládá `wszKeyContainer` se, že kontejner klíčů určený podle je obsahující dvojici klíčů.  
  
 `cbKeyBlob`  
 [v] Velikost v bajtů `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Ukazatel na umístění, do kterého běžný jazyk runtime vrátí podpis. Pokud `ppbSignatureBlob` je null, runtime ukládá podpis v `wszFilePath`souboru určeném .  
  
 Pokud `ppbSignatureBlob` není null, běžný jazyk common time přiděluje místo, ve kterém chcete vrátit podpis. Volající musí uvolnit toto místo pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbSignatureBlob`  
 [out] Velikost vráceného podpisu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`po úspěšném dokončení; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Zadejte `wszFilePath` hodnotu null pro výpočet velikosti podpisu bez vytvoření podpisu.  
  
 Podpis může být uložen buď přímo v souboru, nebo vrácen volajícímu.  
  
 Pokud `StrongNameSignatureGeneration` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameSignatureGeneration – metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx – metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

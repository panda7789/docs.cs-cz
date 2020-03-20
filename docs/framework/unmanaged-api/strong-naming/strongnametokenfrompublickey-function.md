---
title: StrongNameTokenFromPublicKey – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175054"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey – funkce
Získá token představující veřejný klíč. Token silného názvu je zkrácená forma veřejného klíče.  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [v] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) který obsahuje veřejnou část dvojice klíčů slouží ke generování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 [v] Velikost v bajtů `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Token silného názvu odpovídající klíči předaný v `pbPublicKeyBlob`. Běžný jazyk runtime přiděluje paměť, ve kterém chcete vrátit token. Volající musí uvolnit tuto paměť pomocí funkce [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbStrongNameToken`  
 [out] Velikost tokenu vráceného silného názvu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`po úspěšném dokončení; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácená forma veřejného klíče, který slouží k úspoře místa při ukládání informací o klíči v metadatech. Konkrétně tokeny silného názvu se používají v odkazech na sestavení odkazovat na závislé sestavení.  
  
 Pokud `StrongNameTokenFromPublicKey` se funkce nedokončí úspěšně, zavolejte funkci [StrongNameErrorInfo,](strongnameerrorinfo-function.md) abyste načetli poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako zdroj v souboru mscoree.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameTokenFromPublicKey – metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey – metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob – struktura](publickeyblob-structure.md)

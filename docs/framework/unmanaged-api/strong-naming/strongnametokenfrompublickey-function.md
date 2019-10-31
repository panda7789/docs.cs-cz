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
ms.openlocfilehash: b95c96efeb666f25d04118aa8cb9b0da3a2e7924
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104166"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey – funkce
Získá token představující veřejný klíč. Token silného názvu je zkrácenou formou veřejného klíče.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromPublicKey –](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .  
  
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
 pro Struktura typu [PublicKeyBlob –](publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.  
  
 `cbPublicKeyBlob`  
 pro Velikost `pbPublicKeyBlob`v bajtech.  
  
 `ppbStrongNameToken`  
 mimo Token silného názvu odpovídající klíči předanému `pbPublicKeyBlob`. Modul CLR (Common Language Runtime) přiděluje paměť, ve které má být token vrácen. Volající musí uvolnit tuto paměť pomocí funkce [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) .  
  
 `pcbStrongNameToken`  
 mimo Velikost vráceného tokenu silného názvu (v bajtech)  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácený tvar veřejného klíče, který slouží k ukládání místa při ukládání klíčových informací v metadatech. Konkrétně tokeny se silným názvem se používají v odkazech na sestavení pro odkazování na závislé sestavení.  
  
 Pokud se funkce `StrongNameTokenFromPublicKey` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameTokenFromPublicKey – metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey – metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob – struktura](publickeyblob-structure.md)

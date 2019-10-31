---
title: StrongNameTokenFromAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104238"
---
# <a name="strongnametokenfromassemblyex-function"></a>StrongNameTokenFromAssemblyEx – funkce
Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč, který token představuje.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromAssemblyEx –](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.  
  
 `ppbStrongNameToken`  
 mimo Vrácený token silného názvu.  
  
 `pcbStrongNameToken`  
 mimo Velikost tokenu silného názvu v bajtech.  
  
 `ppbPublicKeyBlob`  
 mimo Vrácený veřejný klíč.  
  
 `pcbPublicKeyBlob`  
 mimo Velikost veřejného klíče v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácenou formou veřejného klíče. Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení. Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.  
  
 Po načtení klíče a vytvoření tokenu byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.  
  
 Pokud se funkce `StrongNameTokenFromAssemblyEx` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameTokenFromAssemblyEx – metoda](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [StrongNameTokenFromAssembly – metoda](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

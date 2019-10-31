---
title: StrongNameTokenFromAssembly – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121135"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly – funkce
Vytvoří ze zadaného souboru sestavení token se silným názvem.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromAssembly –](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.  
  
 `ppbStrongNameToken`  
 mimo Vrácený token silného názvu.  
  
 `pcbStrongNameToken`  
 mimo Velikost tokenu silného názvu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` po úspěšném dokončení; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Token silného názvu je zkrácenou formou veřejného klíče. Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení. Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.  
  
 Po vytvoření tokenu byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.  
  
 Pokud se funkce `StrongNameTokenFromAssembly` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameTokenFromAssembly – metoda](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx – metoda](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

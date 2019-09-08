---
title: StrongNameCompareAssemblies – funkce
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c2e8e46c7bb3a5e693c9ea16e6c5a0722b1898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799147"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies – funkce
Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.  
  
 Tato funkce je zastaralá. Místo toho použijte metodu [ICLRStrongName:: StrongNameCompareAssemblies –](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 pro Cesta k prvnímu sestavení  
  
 `wszAssembly2`  
 pro Cesta k druhému sestavení  
  
 `pdwResult`  
 mimo Jedna z následujících hodnot:  
  
- `SN_CMP_DIFFERENT`(0) – určuje, že sestavení obsahují jiná data.  
  
- `SN_CMP_IDENTICAL`(1) – určuje, že sestavení jsou přesně stejná, včetně jejich podpisů a kontrolního součtu.  
  
- `SN_CMP_SIGONLY`(2) – určuje, že sestavení se liší pouze pomocí signatury a kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Po úspěšném dokončení; v opačném případě. `false`  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Podpis silného názvu sestavení se skládá z textového názvu sestavení, verze, jazykové verze a tokenu veřejného klíče.  
  
 Pokud se `StrongNameCompareAssemblies` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.  
  
## <a name="see-also"></a>Viz také:

- [StrongNameCompareAssemblies – metoda](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)

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
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000321"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies – funkce
Určuje, zda se dvě sestavení liší pouze v jejich podpisy se silným názvem.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamecompareassemblies –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 [in] Cesta k sestavení první.  
  
 `wszAssembly2`  
 [in] Cesta k druhé sestavení.  
  
 `pdwResult`  
 [out] Jeden z následujících hodnot:  
  
- `SN_CMP_DIFFERENT` (0) – určuje, zda sestavení obsahovat různé datové.  
  
- `SN_CMP_IDENTICAL` (1) – určuje, že sestavení jsou stejné, včetně jejich podpisy a kontrolního součtu.  
  
- `SN_CMP_SIGONLY` (2) – určuje, že sestavení liší pouze v podpisu a kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Při úspěšném dokončení; v opačném případě `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Podpis silného názvu sestavení se skládá z textový název sestavení, verzi, jazykovou verzi a token veřejného klíče.  
  
 Pokud `StrongNameCompareAssemblies` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.  
  
## <a name="see-also"></a>Viz také:

- [StrongNameCompareAssemblies – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

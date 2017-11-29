---
title: "StrongNameCompareAssemblies – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3453cffb5e98e3623565785ab64db4f455be981
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies – funkce
Určuje, zda dva sestavení liší pouze jejich podpisy silným názvem.  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamecompareassemblies –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 [v] Cesta k první sestavení.  
  
 `wszAssembly2`  
 [v] Cesta k sestavení druhý.  
  
 `pdwResult`  
 [out] Jedna z následujících hodnot:  
  
-   `SN_CMP_DIFFERENT`(0) - určuje, že sestavení obsahovat různé data.  
  
-   `SN_CMP_IDENTICAL`(1) - určuje, že sestavení jsou stejné, včetně jejich podpisy a kontrolního součtu.  
  
-   `SN_CMP_SIGONLY`(2) - určuje, že sestavení liší pouze podpisu a kontrolních součtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Při úspěšném dokončení; v opačném `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Podpis silného názvu sestavení se skládá z textu název sestavení, verzi, jazykovou verzi a tokenu veřejného klíče.  
  
 Pokud `StrongNameCompareAssemblies` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.  
  
## <a name="see-also"></a>Viz také  
 [Strongnamecompareassemblies – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [Iclrstrongname – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

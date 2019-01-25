---
title: IsFrameworkAssembly – funkce
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e231c4fa51e6e66cba6227233cf73dd1cd4ebbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733919"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly – funkce
Získá hodnotu, která určuje, zda se spravuje zadané sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzAssemblyReference`  
 [in] Název sestavení ke kontrole.  
  
 `pbIsFrameworkAssembly`  
 [out] Logická hodnota, která určuje, jestli je spravované sestavení.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.  
  
 `pccSize`  
 [in] Velikost `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Poznámky  
 `pwzAssemblyReference` Parametrem je ukazatel na řetězec znaků, který obsahuje název sestavení.  
  
 Pokud je toto sestavení součástí .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat hodnotu typu Boolean `true`.  
  
 Pokud pojmenované sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` sestavení, nikoli název parametru `pbIsFrameworkAssembly` bude obsahovat hodnotu typu Boolean `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Viz také:
- [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

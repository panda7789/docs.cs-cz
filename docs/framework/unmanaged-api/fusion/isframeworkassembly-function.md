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
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429247"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly – funkce
Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.  
  
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
 [v] Název sestavení, které chcete zkontrolovat.  
  
 `pbIsFrameworkAssembly`  
 [out] Logická hodnota, která určuje, jestli je sestavení spravuje.  
  
 `pwzFrameworkAssemblyIdentity`  
 [v] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.  
  
 `pccSize`  
 [v] Velikost `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Poznámky  
 `pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.  
  
 Pokud je toto sestavení součástí rozhraní .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat logickou hodnotu z `true`.  
  
 Pokud pojmenovaný sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` parametr není název sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu z `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

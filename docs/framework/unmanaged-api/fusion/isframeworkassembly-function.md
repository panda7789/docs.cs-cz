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
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123072"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly – funkce
Získá hodnotu, která označuje, zda je zadané sestavení spravováno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyReference`  
 pro Název sestavení, které má být zkontrolováno.  
  
 `pbIsFrameworkAssembly`  
 mimo Logická hodnota, která určuje, zda je sestavení spravováno.  
  
 `pwzFrameworkAssemblyIdentity`  
 pro Nekanonický řetězec, který obsahuje jedinečnou identitu sestavení.  
  
 `pccSize`  
 pro Velikost `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Poznámky  
 Parametr `pwzAssemblyReference` je ukazatel na řetězec znaků, který obsahuje název sestavení.  
  
 Pokud je toto sestavení součástí .NET Framework, parametr `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu `true`.  
  
 Pokud pojmenované sestavení není součástí .NET Framework, nebo pokud parametr `pwzAssemblyReference` nejmenuje sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

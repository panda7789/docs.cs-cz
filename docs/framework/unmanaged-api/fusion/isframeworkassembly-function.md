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
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796313"
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
 `pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.  
  
 Pokud je toto sestavení součástí .NET Framework, `pbIsFrameworkAssembly` parametr bude obsahovat logickou `true`hodnotu.  
  
 Pokud pojmenované sestavení není součástí .NET Framework, nebo pokud `pwzAssemblyReference` parametr nejmenuje sestavení, `pbIsFrameworkAssembly` bude `false`obsahovat logickou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro fúze](fusion-global-static-functions.md)

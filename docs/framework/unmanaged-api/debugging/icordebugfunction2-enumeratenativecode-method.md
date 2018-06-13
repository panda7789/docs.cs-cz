---
title: ICorDebugFunction2::EnumerateNativeCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4d15d9ae63e63f98ab73e250df558dfa16002a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411785"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode – metoda
Icordebugcodeenum – objektu, která obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt ICorDebugFunction2 získá ukazatele rozhraní.  
  
> [!NOTE]
>  `EnumerateNativeCode` v aktuální verzi rozhraní .NET Framework není implementováno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorDebug.idl, CorDebug.h

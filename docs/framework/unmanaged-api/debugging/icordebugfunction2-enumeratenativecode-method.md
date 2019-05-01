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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959962"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode – metoda
Získá ukazatel rozhraní na icordebugcodeenum – objekt, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt icordebugfunction2 –.  
  
> [!NOTE]
>  `EnumerateNativeCode` není implementováno v aktuální verzi rozhraní .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorDebug.idl, CorDebug.h

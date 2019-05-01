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
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="c85b1-102">ICorDebugFunction2::EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="c85b1-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="c85b1-103">Získá ukazatel rozhraní na icordebugcodeenum – objekt, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt icordebugfunction2 –.</span><span class="sxs-lookup"><span data-stu-id="c85b1-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c85b1-104">`EnumerateNativeCode` není implementováno v aktuální verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c85b1-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c85b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c85b1-105">Syntax</span></span>  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c85b1-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c85b1-106">Requirements</span></span>  
 <span data-ttu-id="c85b1-107">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c85b1-107">**Header:** CorDebug.idl, CorDebug.h</span></span>

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
ms.openlocfilehash: fb7e2ed7b076cfa20064902b3592c8f958efc0ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917041"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="26138-102">ICorDebugFunction2::EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="26138-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="26138-103">Získá ukazatel rozhraní na objekt ICorDebugCodeEnum, který obsahuje příkazy nativního kódu ve funkci, na kterou odkazuje tento objekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="26138-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26138-104">`EnumerateNativeCode`není implementován v aktuální verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26138-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26138-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26138-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="26138-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26138-106">Requirements</span></span>  
 <span data-ttu-id="26138-107">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26138-107">**Header:** CorDebug.idl, CorDebug.h</span></span>

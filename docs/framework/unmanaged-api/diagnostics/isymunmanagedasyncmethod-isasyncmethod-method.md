---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 460d6781405b6042262d50e1aa79ee8c77f781a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489719"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="b47bf-102">ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="b47bf-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="b47bf-103">Kontroluje, jestli metoda má asynchronní informace, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b47bf-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="b47bf-104">Pokud tato metoda vrátí `FALSE` je volat jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b47bf-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b47bf-105">Budou všechny návratové `E_UNEXPECTED` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="b47bf-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47bf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b47bf-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b47bf-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b47bf-107">Parameters</span></span>  
  
|<span data-ttu-id="b47bf-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="b47bf-108">Parameter</span></span>|<span data-ttu-id="b47bf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b47bf-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="b47bf-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b47bf-110">Return Value</span></span>  
 <span data-ttu-id="b47bf-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="b47bf-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b47bf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b47bf-112">Requirements</span></span>  
 <span data-ttu-id="b47bf-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b47bf-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47bf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b47bf-114">See also</span></span>
- [<span data-ttu-id="b47bf-115">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b47bf-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

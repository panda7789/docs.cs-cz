---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129214"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="7abc4-102">ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7abc4-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="7abc4-103">Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="7abc4-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="7abc4-104">Pokud tato metoda vrátí `FALSE` pak je neplatná pro volání jakékoli jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7abc4-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="7abc4-105">Budou v tomto případě vráceny `E_UNEXPECTED`.</span><span class="sxs-lookup"><span data-stu-id="7abc4-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abc4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7abc4-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abc4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7abc4-107">Parameters</span></span>  
  
|<span data-ttu-id="7abc4-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="7abc4-108">Parameter</span></span>|<span data-ttu-id="7abc4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7abc4-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="7abc4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7abc4-110">Return Value</span></span>  
 <span data-ttu-id="7abc4-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7abc4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abc4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7abc4-112">Requirements</span></span>  
 <span data-ttu-id="7abc4-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7abc4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abc4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7abc4-114">See also</span></span>

- [<span data-ttu-id="7abc4-115">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7abc4-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424938"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="1b489-102">ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="1b489-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="1b489-103">Zkontroluje, zda metoda má asynchronní informace, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="1b489-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="1b489-104">Pokud tato metoda vrátí hodnotu `FALSE` , pak je volat jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1b489-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="1b489-105">Ty budou všechny návratové `E_UNEXPECTED` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="1b489-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b489-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b489-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b489-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b489-107">Parameters</span></span>  
  
|<span data-ttu-id="1b489-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="1b489-108">Parameter</span></span>|<span data-ttu-id="1b489-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1b489-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="1b489-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b489-110">Return Value</span></span>  
 <span data-ttu-id="1b489-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1b489-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b489-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b489-112">Requirements</span></span>  
 <span data-ttu-id="1b489-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1b489-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b489-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b489-114">See Also</span></span>  
 [<span data-ttu-id="1b489-115">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b489-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

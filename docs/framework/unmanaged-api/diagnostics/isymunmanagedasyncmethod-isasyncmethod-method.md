---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441796"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="c520e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="c520e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="c520e-103">Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="c520e-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="c520e-104">Pokud se tato metoda vrátí `FALSE` , je neplatná pro volání jakékoli jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c520e-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c520e-105">Budou `E_UNEXPECTED` v tomto případě vráceny.</span><span class="sxs-lookup"><span data-stu-id="c520e-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c520e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c520e-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c520e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c520e-107">Parameters</span></span>  
  
|<span data-ttu-id="c520e-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="c520e-108">Parameter</span></span>|<span data-ttu-id="c520e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c520e-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="c520e-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c520e-110">Return Value</span></span>  
 <span data-ttu-id="c520e-111">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c520e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c520e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c520e-112">Requirements</span></span>  
 <span data-ttu-id="c520e-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c520e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c520e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c520e-114">See also</span></span>

- [<span data-ttu-id="c520e-115">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c520e-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)

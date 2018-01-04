---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 560690e95e7aa0aef37e3a708183641bd70ee97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="47533-102">ISymUnmanagedAsyncMethod::IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="47533-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="47533-103">Zkontroluje, zda metoda má asynchronní informace, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="47533-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="47533-104">Pokud tato metoda vrátí hodnotu `FALSE` , pak je volat jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47533-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="47533-105">Ty budou všechny návratové `E_UNEXPECTED` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="47533-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47533-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47533-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47533-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="47533-107">Parameters</span></span>  
  
|<span data-ttu-id="47533-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="47533-108">Parameter</span></span>|<span data-ttu-id="47533-109">Popis</span><span class="sxs-lookup"><span data-stu-id="47533-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="47533-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47533-110">Return Value</span></span>  
 <span data-ttu-id="47533-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="47533-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47533-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47533-112">Requirements</span></span>  
 <span data-ttu-id="47533-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47533-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47533-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="47533-114">See Also</span></span>  
 [<span data-ttu-id="47533-115">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47533-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

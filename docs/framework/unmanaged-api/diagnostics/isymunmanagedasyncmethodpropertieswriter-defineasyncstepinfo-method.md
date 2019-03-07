---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bac541909e07aadff06006fba8c3cfcf4dc5465
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486222"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="bfc27-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="bfc27-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="bfc27-103">Definujte skupinu asynchronního await operací v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="bfc27-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="bfc27-104">Každý yield posun odpovídá návratový instrukce await, identifikace možných yield.</span><span class="sxs-lookup"><span data-stu-id="bfc27-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="bfc27-105">Každý `breakpointMethod` / `breakpointOffset` pár víme, kde asynchronní operace bude pokračovat, které by mohly být v jiné metody.</span><span class="sxs-lookup"><span data-stu-id="bfc27-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc27-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfc27-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfc27-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfc27-107">Parameters</span></span>  
  
|<span data-ttu-id="bfc27-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="bfc27-108">Parameter</span></span>|<span data-ttu-id="bfc27-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bfc27-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="bfc27-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bfc27-110">Return Value</span></span>  
 <span data-ttu-id="bfc27-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bfc27-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfc27-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bfc27-112">Requirements</span></span>  
 <span data-ttu-id="bfc27-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfc27-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc27-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfc27-114">See also</span></span>
- [<span data-ttu-id="bfc27-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfc27-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

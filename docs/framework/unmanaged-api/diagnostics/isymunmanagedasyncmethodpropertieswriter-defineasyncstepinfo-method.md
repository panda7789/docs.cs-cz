---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8305d0a562fd90e3fae32e372b663ca3942d2a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940137"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="9dbb3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9dbb3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="9dbb3-103">Definujte skupinu asynchronního await operací v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="9dbb3-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="9dbb3-104">Každý yield posun odpovídá návratový instrukce await, identifikace možných yield.</span><span class="sxs-lookup"><span data-stu-id="9dbb3-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="9dbb3-105">Každý `breakpointMethod` / `breakpointOffset` pár víme, kde asynchronní operace bude pokračovat, které by mohly být v jiné metody.</span><span class="sxs-lookup"><span data-stu-id="9dbb3-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dbb3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dbb3-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dbb3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dbb3-107">Parameters</span></span>  
  
|<span data-ttu-id="9dbb3-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="9dbb3-108">Parameter</span></span>|<span data-ttu-id="9dbb3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9dbb3-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="9dbb3-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9dbb3-110">Return Value</span></span>  
 <span data-ttu-id="9dbb3-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9dbb3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dbb3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dbb3-112">Requirements</span></span>  
 <span data-ttu-id="9dbb3-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9dbb3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbb3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dbb3-114">See also</span></span>

- [<span data-ttu-id="9dbb3-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dbb3-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebd4bb1d674a27785ccbe5460a65fed764638ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435874"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="efa57-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="efa57-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="efa57-103">Definujte skupinu asynchronních operací v aktuální metoda await.</span><span class="sxs-lookup"><span data-stu-id="efa57-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="efa57-104">Každý yield posun odpovídá návratový instrukce await, identifikace potenciální upozornění.</span><span class="sxs-lookup"><span data-stu-id="efa57-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="efa57-105">Každý `breakpointMethod` / `breakpointOffset` pár víme, kde asynchronní operaci bude pokračovat, (která může mít jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="efa57-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efa57-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efa57-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efa57-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="efa57-107">Parameters</span></span>  
  
|<span data-ttu-id="efa57-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="efa57-108">Parameter</span></span>|<span data-ttu-id="efa57-109">Popis</span><span class="sxs-lookup"><span data-stu-id="efa57-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="efa57-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="efa57-110">Return Value</span></span>  
 <span data-ttu-id="efa57-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="efa57-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efa57-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efa57-112">Requirements</span></span>  
 <span data-ttu-id="efa57-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="efa57-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa57-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="efa57-114">See Also</span></span>  
 [<span data-ttu-id="efa57-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efa57-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129199"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="769c0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="769c0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="769c0-103">Definujte skupinu asynchronních operací await v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="769c0-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="769c0-104">Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost.</span><span class="sxs-lookup"><span data-stu-id="769c0-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="769c0-105">Každý `breakpointMethod`/`breakpointOffset` pár oznamuje, že se asynchronní operace obnoví, což může být jiná metoda.</span><span class="sxs-lookup"><span data-stu-id="769c0-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="769c0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="769c0-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="769c0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="769c0-107">Parameters</span></span>  
  
|<span data-ttu-id="769c0-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="769c0-108">Parameter</span></span>|<span data-ttu-id="769c0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="769c0-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="769c0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="769c0-110">Return Value</span></span>  
 <span data-ttu-id="769c0-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="769c0-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="769c0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="769c0-112">Requirements</span></span>  
 <span data-ttu-id="769c0-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="769c0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769c0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="769c0-114">See also</span></span>

- [<span data-ttu-id="769c0-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="769c0-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

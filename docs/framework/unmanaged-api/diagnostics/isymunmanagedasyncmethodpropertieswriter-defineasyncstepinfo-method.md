---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e305ca13e419a40e9838a46a61fe7a435b7ce56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="273a4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="273a4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="273a4-103">Definujte skupinu asynchronních operací v aktuální metoda await.</span><span class="sxs-lookup"><span data-stu-id="273a4-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="273a4-104">Každý yield posun odpovídá návratový instrukce await, identifikace potenciální upozornění.</span><span class="sxs-lookup"><span data-stu-id="273a4-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="273a4-105">Každý `breakpointMethod` / `breakpointOffset` pár víme, kde asynchronní operaci bude pokračovat, (která může mít jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="273a4-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273a4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="273a4-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="273a4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="273a4-107">Parameters</span></span>  
  
|<span data-ttu-id="273a4-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="273a4-108">Parameter</span></span>|<span data-ttu-id="273a4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="273a4-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="273a4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="273a4-110">Return Value</span></span>  
 <span data-ttu-id="273a4-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="273a4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="273a4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="273a4-112">Requirements</span></span>  
 <span data-ttu-id="273a4-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="273a4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273a4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="273a4-114">See Also</span></span>  
 [<span data-ttu-id="273a4-115">Isymunmanagedasyncmethodpropertieswriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="273a4-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

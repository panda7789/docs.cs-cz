---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441783"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="aee2f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="aee2f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="aee2f-103">Definujte skupinu asynchronních operací await v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="aee2f-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="aee2f-104">Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost.</span><span class="sxs-lookup"><span data-stu-id="aee2f-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="aee2f-105">Každý `breakpointMethod` / `breakpointOffset` pár nás oznamuje, kde se asynchronní operace obnoví, což může být jiná metoda.</span><span class="sxs-lookup"><span data-stu-id="aee2f-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee2f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aee2f-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aee2f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aee2f-107">Parameters</span></span>  
  
|<span data-ttu-id="aee2f-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="aee2f-108">Parameter</span></span>|<span data-ttu-id="aee2f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="aee2f-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="aee2f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aee2f-110">Return Value</span></span>  
 <span data-ttu-id="aee2f-111">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="aee2f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee2f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aee2f-112">Requirements</span></span>  
 <span data-ttu-id="aee2f-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aee2f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee2f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="aee2f-114">See also</span></span>

- [<span data-ttu-id="aee2f-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aee2f-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)

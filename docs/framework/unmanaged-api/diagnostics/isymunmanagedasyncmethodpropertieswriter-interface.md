---
title: "ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd84ea5ee00df3e59d4907cdf97bc36b7f06d993
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="e593e-102">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e593e-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="e593e-103">Umožňuje zadat informace volitelné asynchronní metoda pro každou metodu symbol.</span><span class="sxs-lookup"><span data-stu-id="e593e-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="e593e-104">Vždy používat s otevřenou metoda; To znamená mezi volání [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="e593e-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e593e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e593e-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="e593e-106">Metody</span><span class="sxs-lookup"><span data-stu-id="e593e-106">Methods</span></span>  
 <span data-ttu-id="e593e-107">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="e593e-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e593e-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="e593e-108">Method</span></span>|<span data-ttu-id="e593e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e593e-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e593e-110">Defineasyncstepinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e593e-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="e593e-111">Definujte skupinu asynchronních operací v aktuální metoda await.</span><span class="sxs-lookup"><span data-stu-id="e593e-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="e593e-112">Každý yield posun odpovídá návratový instrukce await, identifikace potenciální upozornění.</span><span class="sxs-lookup"><span data-stu-id="e593e-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="e593e-113">Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde bude pokračovat asynchronní operaci; může být v jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="e593e-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="e593e-114">Definecatchhandleriloffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e593e-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="e593e-115">Nastaví IL posunutí pro generované kompilátorem catch obslužná rutina, která zabalí asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="e593e-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="e593e-116">Posun IL generovaného catch je používán ladicího programu pro zpracování catch, jako by šlo bez uživatelského kódu, i když může dojít v metodu kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="e593e-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="e593e-117">Konkrétně se používá v reakci **CatchHandlerFound** události výjimky.</span><span class="sxs-lookup"><span data-stu-id="e593e-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="e593e-118">Definekickoffmethod – metoda</span><span class="sxs-lookup"><span data-stu-id="e593e-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="e593e-119">Nastaví počáteční metody, která zahájí asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="e593e-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e593e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e593e-120">Requirements</span></span>  
 <span data-ttu-id="e593e-121">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e593e-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e593e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e593e-122">See Also</span></span>  
 [<span data-ttu-id="e593e-123">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e593e-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

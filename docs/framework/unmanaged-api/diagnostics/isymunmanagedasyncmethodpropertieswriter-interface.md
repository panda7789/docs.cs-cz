---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d83270d0e7f5dabff8402f5f81dae20d4457d147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604245"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="279bb-102">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="279bb-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="279bb-103">Můžete zadat volitelný asynchronní informace metody pro každou metodu symbol.</span><span class="sxs-lookup"><span data-stu-id="279bb-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="279bb-104">Vždy používejte otevřené metodou; To znamená, že mezi voláními [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="279bb-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="279bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="279bb-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="279bb-106">Metody</span><span class="sxs-lookup"><span data-stu-id="279bb-106">Methods</span></span>  
 <span data-ttu-id="279bb-107">Toto rozhraní obsahuje následující dvě metody:</span><span class="sxs-lookup"><span data-stu-id="279bb-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="279bb-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="279bb-108">Method</span></span>|<span data-ttu-id="279bb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="279bb-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="279bb-110">DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="279bb-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="279bb-111">Definujte skupinu asynchronního await operací v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="279bb-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="279bb-112">Každý yield posun odpovídá návratový instrukce await, identifikace možných yield.</span><span class="sxs-lookup"><span data-stu-id="279bb-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="279bb-113">Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde asynchronní operace bude pokračovat, může být v jiné metody.</span><span class="sxs-lookup"><span data-stu-id="279bb-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="279bb-114">DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="279bb-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="279bb-115">Nastavuje posun pro obslužnou rutinu catch vygenerovaný kompilátorem, který obtéká asynchronní metody IL.</span><span class="sxs-lookup"><span data-stu-id="279bb-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="279bb-116">Posun IL generovaný catch používá ladicí program na zpracování bloku catch, jako by šlo neuživatelský kód, i v případě, že může dojít v metodě kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="279bb-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="279bb-117">Zejména je použít v odpovědi **CatchHandlerFound** události výjimky.</span><span class="sxs-lookup"><span data-stu-id="279bb-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="279bb-118">DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="279bb-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="279bb-119">Nastaví výchozí metodu, která zahájí asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="279bb-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="279bb-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="279bb-120">Requirements</span></span>  
 <span data-ttu-id="279bb-121">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="279bb-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279bb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="279bb-122">See also</span></span>
- [<span data-ttu-id="279bb-123">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="279bb-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

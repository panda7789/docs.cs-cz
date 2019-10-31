---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129152"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="60c71-102">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60c71-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="60c71-103">Umožňuje definovat nepovinné informace o asynchronních metodách pro každý symbol metody.</span><span class="sxs-lookup"><span data-stu-id="60c71-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="60c71-104">Vždy používat s otevřenou metodou; To znamená, že mezi voláními [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [metodou CloseMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="60c71-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c71-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60c71-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="60c71-106">Metody</span><span class="sxs-lookup"><span data-stu-id="60c71-106">Methods</span></span>  
 <span data-ttu-id="60c71-107">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="60c71-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="60c71-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="60c71-108">Method</span></span>|<span data-ttu-id="60c71-109">Popis</span><span class="sxs-lookup"><span data-stu-id="60c71-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60c71-110">DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="60c71-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="60c71-111">Definujte skupinu asynchronních operací await v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="60c71-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="60c71-112">Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost.</span><span class="sxs-lookup"><span data-stu-id="60c71-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="60c71-113">Každý `breakpointMethod`/`breakpointOffset` páry identifikuje, kde bude asynchronní operace pokračovat; může se jednat o jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="60c71-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="60c71-114">DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="60c71-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="60c71-115">Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="60c71-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="60c71-116">Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když k tomu může dojít v metodě uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="60c71-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="60c71-117">Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.</span><span class="sxs-lookup"><span data-stu-id="60c71-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="60c71-118">DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="60c71-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="60c71-119">Nastaví počáteční metodu, která inicializuje asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="60c71-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60c71-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60c71-120">Requirements</span></span>  
 <span data-ttu-id="60c71-121">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="60c71-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c71-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60c71-122">See also</span></span>

- [<span data-ttu-id="60c71-123">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="60c71-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

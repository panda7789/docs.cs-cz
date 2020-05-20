---
title: ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 360d1150b0accd6a070fa36531e570d222787cee
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441757"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="cb453-102">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb453-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="cb453-103">Umožňuje definovat nepovinné informace o asynchronních metodách pro každý symbol metody.</span><span class="sxs-lookup"><span data-stu-id="cb453-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="cb453-104">Vždy používat s otevřenou metodou; To znamená, že mezi voláními [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) a [metodou CloseMethod –](isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="cb453-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb453-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb453-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="cb453-106">Metody</span><span class="sxs-lookup"><span data-stu-id="cb453-106">Methods</span></span>  
 <span data-ttu-id="cb453-107">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="cb453-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="cb453-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb453-108">Method</span></span>|<span data-ttu-id="cb453-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb453-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb453-110">DefineAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cb453-110">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="cb453-111">Definujte skupinu asynchronních operací await v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="cb453-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="cb453-112">Každý posun výtěžnosti odpovídá instrukci vracené zpět, která identifikuje potenciální výtěžnost.</span><span class="sxs-lookup"><span data-stu-id="cb453-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="cb453-113">Každý `breakpointMethod` / `breakpointOffset` pár identifikuje, kde se asynchronní operace obnoví; může to být jiná metoda.</span><span class="sxs-lookup"><span data-stu-id="cb453-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="cb453-114">DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cb453-114">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="cb453-115">Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="cb453-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="cb453-116">Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když k tomu může dojít v metodě uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="cb453-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="cb453-117">Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.</span><span class="sxs-lookup"><span data-stu-id="cb453-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="cb453-118">DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="cb453-118">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="cb453-119">Nastaví počáteční metodu, která inicializuje asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="cb453-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb453-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb453-120">Requirements</span></span>  
 <span data-ttu-id="cb453-121">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cb453-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb453-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb453-122">See also</span></span>

- [<span data-ttu-id="cb453-123">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="cb453-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)

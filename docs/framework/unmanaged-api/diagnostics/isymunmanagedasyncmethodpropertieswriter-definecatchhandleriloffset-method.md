---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196746"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="a4bb4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a4bb4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="a4bb4-103">Nastavuje posun pro obslužnou rutinu catch vygenerovaný kompilátorem, který obtéká asynchronní metody IL.</span><span class="sxs-lookup"><span data-stu-id="a4bb4-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="a4bb4-104">Posun IL generovaný catch používá ladicí program na zpracování bloku catch, jako by šlo neuživatelském kódu i v případě, že může dojít k v metodě kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="a4bb4-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="a4bb4-105">Zejména je použít v odpovědi **CatchHandlerFound** události výjimky.</span><span class="sxs-lookup"><span data-stu-id="a4bb4-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4bb4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4bb4-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4bb4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4bb4-107">Parameters</span></span>  
  
|<span data-ttu-id="a4bb4-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="a4bb4-108">Parameter</span></span>|<span data-ttu-id="a4bb4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a4bb4-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="a4bb4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4bb4-110">Return Value</span></span>  
 <span data-ttu-id="a4bb4-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="a4bb4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4bb4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4bb4-112">Requirements</span></span>  
 <span data-ttu-id="a4bb4-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a4bb4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4bb4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4bb4-114">See also</span></span>

- [<span data-ttu-id="a4bb4-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4bb4-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

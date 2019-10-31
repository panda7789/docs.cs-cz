---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129179"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="44ef1-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="44ef1-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="44ef1-103">Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="44ef1-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="44ef1-104">Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když se může vyskytovat v metodě uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="44ef1-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="44ef1-105">Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.</span><span class="sxs-lookup"><span data-stu-id="44ef1-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ef1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44ef1-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44ef1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="44ef1-107">Parameters</span></span>  
  
|<span data-ttu-id="44ef1-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="44ef1-108">Parameter</span></span>|<span data-ttu-id="44ef1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="44ef1-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="44ef1-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44ef1-110">Return Value</span></span>  
 <span data-ttu-id="44ef1-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="44ef1-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ef1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44ef1-112">Requirements</span></span>  
 <span data-ttu-id="44ef1-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="44ef1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ef1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44ef1-114">See also</span></span>

- [<span data-ttu-id="44ef1-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44ef1-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

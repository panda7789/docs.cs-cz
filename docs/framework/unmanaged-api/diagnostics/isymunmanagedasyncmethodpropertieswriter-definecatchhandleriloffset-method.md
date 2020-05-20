---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441770"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="f08d2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f08d2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="f08d2-103">Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="f08d2-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="f08d2-104">Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když se může vyskytovat v metodě uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="f08d2-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="f08d2-105">Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.</span><span class="sxs-lookup"><span data-stu-id="f08d2-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f08d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f08d2-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f08d2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f08d2-107">Parameters</span></span>  
  
|<span data-ttu-id="f08d2-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="f08d2-108">Parameter</span></span>|<span data-ttu-id="f08d2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f08d2-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="f08d2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f08d2-110">Return Value</span></span>  
 <span data-ttu-id="f08d2-111">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="f08d2-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08d2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f08d2-112">Requirements</span></span>  
 <span data-ttu-id="f08d2-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f08d2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08d2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f08d2-114">See also</span></span>

- [<span data-ttu-id="f08d2-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f08d2-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)

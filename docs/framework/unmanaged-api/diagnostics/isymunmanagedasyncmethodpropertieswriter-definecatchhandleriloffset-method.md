---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425428"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="1c1c7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1c1c7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="1c1c7-103">Nastaví IL posunutí pro generované kompilátorem catch obslužná rutina, která zabalí asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="1c1c7-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="1c1c7-104">Posun IL generovaného catch je používán ladicího programu pro zpracování catch, jako by šlo bez uživatelského kódu, i když můžou nastat ve metodu kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="1c1c7-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="1c1c7-105">Konkrétně se používá v reakci **CatchHandlerFound** události výjimky.</span><span class="sxs-lookup"><span data-stu-id="1c1c7-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c1c7-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c1c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c1c7-107">Parameters</span></span>  
  
|<span data-ttu-id="1c1c7-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="1c1c7-108">Parameter</span></span>|<span data-ttu-id="1c1c7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1c1c7-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="1c1c7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1c1c7-110">Return Value</span></span>  
 <span data-ttu-id="1c1c7-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1c1c7-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c1c7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c1c7-112">Requirements</span></span>  
 <span data-ttu-id="1c1c7-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1c1c7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1c7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c1c7-114">See Also</span></span>  
 [<span data-ttu-id="1c1c7-115">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c1c7-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

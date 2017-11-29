---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3bae0e2dfb56883a674b282acd385ba45a25bebb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="f8cc2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f8cc2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="f8cc2-103">Nastaví IL posunutí pro generované kompilátorem catch obslužná rutina, která zabalí asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="f8cc2-104">Posun IL generovaného catch je používán ladicího programu pro zpracování catch, jako by šlo bez uživatelského kódu, i když můžou nastat ve metodu kódu uživatele.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="f8cc2-105">Konkrétně se používá v reakci **CatchHandlerFound** události výjimky.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8cc2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8cc2-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8cc2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8cc2-107">Parameters</span></span>  
  
|<span data-ttu-id="f8cc2-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="f8cc2-108">Parameter</span></span>|<span data-ttu-id="f8cc2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f8cc2-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="f8cc2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8cc2-110">Return Value</span></span>  
 <span data-ttu-id="f8cc2-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8cc2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8cc2-112">Requirements</span></span>  
 <span data-ttu-id="f8cc2-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8cc2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cc2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8cc2-114">See Also</span></span>  
 [<span data-ttu-id="f8cc2-115">Isymunmanagedasyncmethodpropertieswriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8cc2-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

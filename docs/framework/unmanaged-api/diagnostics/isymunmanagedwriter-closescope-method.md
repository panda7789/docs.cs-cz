---
title: ISymUnmanagedWriter::CloseScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 264b4487483ed5439a9809feefcdc1b20af402dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428073"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="70f6f-102">ISymUnmanagedWriter::CloseScope – metoda</span><span class="sxs-lookup"><span data-stu-id="70f6f-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="70f6f-103">Closes the current lexical scope.</span><span class="sxs-lookup"><span data-stu-id="70f6f-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70f6f-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70f6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70f6f-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="70f6f-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span><span class="sxs-lookup"><span data-stu-id="70f6f-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70f6f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70f6f-107">Return Value</span></span>  
 <span data-ttu-id="70f6f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="70f6f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f6f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70f6f-109">Remarks</span></span>  
 <span data-ttu-id="70f6f-110">Once a scope is closed, no more variables can be defined within it.</span><span class="sxs-lookup"><span data-stu-id="70f6f-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="70f6f-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span><span class="sxs-lookup"><span data-stu-id="70f6f-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="70f6f-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span><span class="sxs-lookup"><span data-stu-id="70f6f-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="70f6f-113">Scope identifiers are valid only in the current method.</span><span class="sxs-lookup"><span data-stu-id="70f6f-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f6f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70f6f-114">Requirements</span></span>  
 <span data-ttu-id="70f6f-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="70f6f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f6f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70f6f-116">See also</span></span>

- [<span data-ttu-id="70f6f-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70f6f-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

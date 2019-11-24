---
title: ISymUnmanagedWriter::Close – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: cd601ac6041ca22d59d7467bafc7c1d87b21371f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428110"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="bc62e-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="bc62e-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="bc62e-103">Closes the symbol writer after committing the symbols to the symbol store.</span><span class="sxs-lookup"><span data-stu-id="bc62e-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc62e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc62e-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bc62e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc62e-105">Return Value</span></span>  
 <span data-ttu-id="bc62e-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="bc62e-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc62e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc62e-107">Remarks</span></span>  
 <span data-ttu-id="bc62e-108">After this call, the symbol writer becomes invalid for further updates.</span><span class="sxs-lookup"><span data-stu-id="bc62e-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="bc62e-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span><span class="sxs-lookup"><span data-stu-id="bc62e-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc62e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc62e-110">Requirements</span></span>  
 <span data-ttu-id="bc62e-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bc62e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc62e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc62e-112">See also</span></span>

- [<span data-ttu-id="bc62e-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc62e-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

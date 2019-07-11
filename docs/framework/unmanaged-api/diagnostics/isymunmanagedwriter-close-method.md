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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd7131c55f9c06a8fcfc0cad859c18e410169c78
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778205"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="7ca71-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca71-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="7ca71-103">Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbol.</span><span class="sxs-lookup"><span data-stu-id="7ca71-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ca71-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7ca71-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ca71-105">Return Value</span></span>  
 <span data-ttu-id="7ca71-106">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7ca71-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca71-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ca71-107">Remarks</span></span>  
 <span data-ttu-id="7ca71-108">Po tomto volání zapisovač symbol stává neplatným další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="7ca71-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="7ca71-109">Zapisovač symbol okno zavřít bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="7ca71-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca71-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ca71-110">Requirements</span></span>  
 <span data-ttu-id="7ca71-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ca71-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca71-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ca71-112">See also</span></span>

- [<span data-ttu-id="7ca71-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ca71-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

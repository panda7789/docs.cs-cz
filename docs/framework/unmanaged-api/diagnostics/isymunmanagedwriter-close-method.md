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
ms.openlocfilehash: 780c19acd3d6980c0fb3e31d01e569a61fd04d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647306"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="a8234-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="a8234-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="a8234-103">Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbol.</span><span class="sxs-lookup"><span data-stu-id="a8234-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8234-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a8234-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8234-105">Return Value</span></span>  
 <span data-ttu-id="a8234-106">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a8234-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8234-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8234-107">Remarks</span></span>  
 <span data-ttu-id="a8234-108">Po tomto volání zapisovač symbol stává neplatným další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a8234-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="a8234-109">Zapisovač symbol okno zavřít bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a8234-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8234-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8234-110">Requirements</span></span>  
 <span data-ttu-id="a8234-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a8234-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8234-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8234-112">See also</span></span>
- [<span data-ttu-id="a8234-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8234-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

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
ms.openlocfilehash: 30747fa25528f5679264ebfb67addf401b7d01d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426326"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="a9777-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="a9777-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="a9777-103">Zavře zapisovače symbol po potvrzení symboly pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="a9777-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9777-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9777-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a9777-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9777-105">Return Value</span></span>  
 <span data-ttu-id="a9777-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a9777-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9777-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9777-107">Remarks</span></span>  
 <span data-ttu-id="a9777-108">Po toto volání zapisovače symbol stává neplatným pro další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a9777-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="a9777-109">Zavřete modul pro zápis symbol bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a9777-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9777-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9777-110">Requirements</span></span>  
 <span data-ttu-id="a9777-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9777-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9777-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9777-112">See Also</span></span>  
 [<span data-ttu-id="a9777-113">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9777-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

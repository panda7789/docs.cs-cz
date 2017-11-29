---
title: "ISymUnmanagedWriter::Close – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Close
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad0cec59531a7e22d0a4d2220cb2dfcdd8f27596
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="c0ff8-102">ISymUnmanagedWriter::Close – metoda</span><span class="sxs-lookup"><span data-stu-id="c0ff8-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="c0ff8-103">Zavře zapisovače symbol po potvrzení symboly pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="c0ff8-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ff8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0ff8-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c0ff8-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0ff8-105">Return Value</span></span>  
 <span data-ttu-id="c0ff8-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c0ff8-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0ff8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0ff8-107">Remarks</span></span>  
 <span data-ttu-id="c0ff8-108">Po toto volání zapisovače symbol stává neplatným pro další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="c0ff8-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="c0ff8-109">Zavřete modul pro zápis symbol bez potvrzení symboly, použijte [isymunmanagedwriter::Abort –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="c0ff8-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ff8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0ff8-110">Requirements</span></span>  
 <span data-ttu-id="c0ff8-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0ff8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ff8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0ff8-112">See Also</span></span>  
 [<span data-ttu-id="c0ff8-113">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0ff8-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

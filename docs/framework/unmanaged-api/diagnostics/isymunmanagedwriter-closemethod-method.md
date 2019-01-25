---
title: ISymUnmanagedWriter::CloseMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6f8c8b522aabfce3b83b6b624bd0ca9757448ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666017"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="7ce78-102">ISymUnmanagedWriter::CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7ce78-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="7ce78-103">Zavře aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="7ce78-103">Closes the current method.</span></span> <span data-ttu-id="7ce78-104">Po zavření metodu žádné další symboly lze definovat v něm.</span><span class="sxs-lookup"><span data-stu-id="7ce78-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce78-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ce78-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7ce78-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ce78-106">Return Value</span></span>  
 <span data-ttu-id="7ce78-107">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7ce78-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce78-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ce78-108">Requirements</span></span>  
 <span data-ttu-id="7ce78-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ce78-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce78-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ce78-110">See also</span></span>
- [<span data-ttu-id="7ce78-111">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ce78-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7ce78-112">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7ce78-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)

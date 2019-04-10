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
ms.openlocfilehash: 591279a80b7d6a770127fb98eb71c056c48bdffd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231211"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="bf095-102">ISymUnmanagedWriter::CloseMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="bf095-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="bf095-103">Zavře aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="bf095-103">Closes the current method.</span></span> <span data-ttu-id="bf095-104">Po zavření metodu žádné další symboly lze definovat v něm.</span><span class="sxs-lookup"><span data-stu-id="bf095-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf095-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf095-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bf095-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf095-106">Return Value</span></span>  
 <span data-ttu-id="bf095-107">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bf095-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf095-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf095-108">Requirements</span></span>  
 <span data-ttu-id="bf095-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bf095-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf095-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf095-110">See also</span></span>

- [<span data-ttu-id="bf095-111">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf095-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="bf095-112">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="bf095-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)

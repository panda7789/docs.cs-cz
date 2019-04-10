---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222676"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="975bf-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans – metoda</span><span class="sxs-lookup"><span data-stu-id="975bf-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="975bf-103">Otevřete část speciální vlastní data a vygenerovat token zdroj značky span mapování informace do.</span><span class="sxs-lookup"><span data-stu-id="975bf-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="975bf-104">Otevírání tohoto oddílu při metody je již otevřen nebo naopak, je chybou.</span><span class="sxs-lookup"><span data-stu-id="975bf-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975bf-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="975bf-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="975bf-106">Return Value</span></span>  
 <span data-ttu-id="975bf-107">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="975bf-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975bf-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="975bf-108">Requirements</span></span>  
 <span data-ttu-id="975bf-109">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="975bf-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975bf-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="975bf-110">See also</span></span>

- [<span data-ttu-id="975bf-111">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="975bf-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)

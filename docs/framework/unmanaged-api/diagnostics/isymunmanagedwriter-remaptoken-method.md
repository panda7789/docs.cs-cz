---
title: "ISymUnmanagedWriter::RemapToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.RemapToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d6c78a49c55bdc9093241952bee00ee331696e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="66e40-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="66e40-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="66e40-103">Upozorní zapisovače symbol, že token metadat jako metadata byla vygenerované složek.</span><span class="sxs-lookup"><span data-stu-id="66e40-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="66e40-104">Pokud zapisovače symbol má uložený staré token v rámci úložiště symbolů, musíte buď aktualizace, které uložené token s novou hodnotu, nebo musíte uložit mapy pro odpovídající čtečku symbol přemapování během čtení fáze.</span><span class="sxs-lookup"><span data-stu-id="66e40-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e40-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66e40-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66e40-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66e40-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="66e40-107">[v] Token metadata, která byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="66e40-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="66e40-108">[v] Nový token metadat, ke kterému `oldToken` byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="66e40-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e40-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66e40-109">Return Value</span></span>  
 <span data-ttu-id="66e40-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="66e40-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e40-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66e40-111">Requirements</span></span>  
 <span data-ttu-id="66e40-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66e40-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e40-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="66e40-113">See Also</span></span>  
 [<span data-ttu-id="66e40-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66e40-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

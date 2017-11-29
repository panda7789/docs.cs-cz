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
ms.openlocfilehash: 857b68c0443e7b23af30ed64ecc9b78af0b40880
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="baf4f-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="baf4f-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="baf4f-103">Upozorní zapisovače symbol, že token metadat jako metadata byla vygenerované složek.</span><span class="sxs-lookup"><span data-stu-id="baf4f-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="baf4f-104">Pokud zapisovače symbol má uložený staré token v rámci úložiště symbolů, musíte buď aktualizace, které uložené token s novou hodnotu, nebo musíte uložit mapy pro odpovídající čtečku symbol přemapování během čtení fáze.</span><span class="sxs-lookup"><span data-stu-id="baf4f-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf4f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baf4f-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="baf4f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="baf4f-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="baf4f-107">[v] Token metadata, která byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="baf4f-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="baf4f-108">[v] Nový token metadat, ke kterému `oldToken` byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="baf4f-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baf4f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="baf4f-109">Return Value</span></span>  
 <span data-ttu-id="baf4f-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="baf4f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf4f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="baf4f-111">Requirements</span></span>  
 <span data-ttu-id="baf4f-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="baf4f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf4f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="baf4f-113">See Also</span></span>  
 [<span data-ttu-id="baf4f-114">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="baf4f-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

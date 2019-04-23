---
title: ISymUnmanagedWriter::RemapToken – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 979d14b4c404c3bf12c427bd5b8b1d4997805e7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160677"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="d27fb-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d27fb-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="d27fb-103">Upozorní zapisovač symbol, že má jako metadata generovalo přemapování token metadat.</span><span class="sxs-lookup"><span data-stu-id="d27fb-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="d27fb-104">Pokud zapisovač symbol má uložené původní token v úložišti symbolů, musí být buď aktualizovat uložené token s novou hodnotu, nebo musíte uložit mapování pro odpovídající modul pro načítání symbolů přemapování další fázi.</span><span class="sxs-lookup"><span data-stu-id="d27fb-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d27fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d27fb-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d27fb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d27fb-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="d27fb-107">[in] Token metadat, která byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="d27fb-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="d27fb-108">[in] Nový token metadat, ke kterému `oldToken` byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="d27fb-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d27fb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d27fb-109">Return Value</span></span>  
 <span data-ttu-id="d27fb-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d27fb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d27fb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d27fb-111">Requirements</span></span>  
 <span data-ttu-id="d27fb-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d27fb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27fb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d27fb-113">See also</span></span>

- [<span data-ttu-id="d27fb-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d27fb-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

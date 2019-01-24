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
ms.openlocfilehash: 0ec3f94d290423130e3718b32cd8058f59d797d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694513"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="1d6dd-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="1d6dd-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="1d6dd-103">Upozorní zapisovač symbol, že má jako metadata generovalo přemapování token metadat.</span><span class="sxs-lookup"><span data-stu-id="1d6dd-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="1d6dd-104">Pokud zapisovač symbol má uložené původní token v úložišti symbolů, musí být buď aktualizovat uložené token s novou hodnotu, nebo musíte uložit mapování pro odpovídající modul pro načítání symbolů přemapování další fázi.</span><span class="sxs-lookup"><span data-stu-id="1d6dd-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d6dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d6dd-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d6dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d6dd-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="1d6dd-107">[in] Token metadat, která byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="1d6dd-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="1d6dd-108">[in] Nový token metadat, ke kterému `oldToken` byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="1d6dd-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d6dd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1d6dd-109">Return Value</span></span>  
 <span data-ttu-id="1d6dd-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1d6dd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d6dd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d6dd-111">Requirements</span></span>  
 <span data-ttu-id="1d6dd-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1d6dd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d6dd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d6dd-113">See also</span></span>
- [<span data-ttu-id="1d6dd-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d6dd-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

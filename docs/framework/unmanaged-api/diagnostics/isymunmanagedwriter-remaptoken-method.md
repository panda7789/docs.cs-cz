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
ms.openlocfilehash: c04ca1d56f3e93c77f335218bb534f890e9053d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776608"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="cc451-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="cc451-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="cc451-103">Upozorní zapisovač symbol, že má jako metadata generovalo přemapování token metadat.</span><span class="sxs-lookup"><span data-stu-id="cc451-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="cc451-104">Pokud zapisovač symbol má uložené původní token v úložišti symbolů, musí být buď aktualizovat uložené token s novou hodnotu, nebo musíte uložit mapování pro odpovídající modul pro načítání symbolů přemapování další fázi.</span><span class="sxs-lookup"><span data-stu-id="cc451-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc451-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc451-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc451-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc451-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="cc451-107">[in] Token metadat, která byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="cc451-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="cc451-108">[in] Nový token metadat, ke kterému `oldToken` byla přeřazena.</span><span class="sxs-lookup"><span data-stu-id="cc451-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc451-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc451-109">Return Value</span></span>  
 <span data-ttu-id="cc451-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cc451-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc451-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc451-111">Requirements</span></span>  
 <span data-ttu-id="cc451-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc451-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc451-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc451-113">See also</span></span>

- [<span data-ttu-id="cc451-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc451-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

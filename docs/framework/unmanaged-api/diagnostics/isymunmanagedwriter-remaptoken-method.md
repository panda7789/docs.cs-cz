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
ms.openlocfilehash: 53cc908e0dc8cc5cc980ec365ccac0df4e620cac
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609765"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="e3c67-102">ISymUnmanagedWriter::RemapToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e3c67-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="e3c67-103">Upozorní zapisovač symbolů, že token metadat byl přemapován, protože byla vygenerována metadata.</span><span class="sxs-lookup"><span data-stu-id="e3c67-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="e3c67-104">Pokud zapisovač symbolů uložil starý token do úložiště symbolů, musí buď aktualizovat uložený token s novou hodnotou, nebo musí uložit mapu pro odpovídající čtečku symbolů k přemapování během fáze čtení.</span><span class="sxs-lookup"><span data-stu-id="e3c67-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c67-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3c67-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c67-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c67-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="e3c67-107">pro Token metadat, který byl přemapován.</span><span class="sxs-lookup"><span data-stu-id="e3c67-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="e3c67-108">pro Nový token metadat, ke kterému `oldToken` bylo přemapováno.</span><span class="sxs-lookup"><span data-stu-id="e3c67-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3c67-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e3c67-109">Return Value</span></span>  
 <span data-ttu-id="e3c67-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e3c67-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c67-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3c67-111">Requirements</span></span>  
 <span data-ttu-id="e3c67-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e3c67-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c67-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3c67-113">See also</span></span>

- [<span data-ttu-id="e3c67-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3c67-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

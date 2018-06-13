---
title: ISymUnmanagedMethod::GetSourceStartEnd – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e15bab136540c73f8e1cff0e6bb52ec1d6c0063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426221"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="d26be-102">ISymUnmanagedMethod::GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="d26be-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="d26be-103">Získá počáteční a koncové pozice dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="d26be-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="d26be-104">První pozice pole je spuštění a druhý pozice pole je end.</span><span class="sxs-lookup"><span data-stu-id="d26be-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d26be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d26be-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d26be-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d26be-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="d26be-107">[v] Počáteční a koncovou zdroj dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d26be-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="d26be-108">[v] Počáteční a koncovou řádky do odpovídajícího zdroje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d26be-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="d26be-109">[v] Počáteční a koncovou sloupce do odpovídajícího zdroje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d26be-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d26be-110">[out] `true` kdyby pozic definován; jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="d26be-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d26be-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d26be-111">Return Value</span></span>  
 <span data-ttu-id="d26be-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d26be-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d26be-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d26be-113">Requirements</span></span>  
 <span data-ttu-id="d26be-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d26be-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26be-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d26be-115">See Also</span></span>  
 [<span data-ttu-id="d26be-116">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d26be-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

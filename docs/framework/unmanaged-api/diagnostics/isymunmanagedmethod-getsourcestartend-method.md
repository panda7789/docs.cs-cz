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
ms.openlocfilehash: a75fed4c46ea7e31177ac0446c8fae7805535323
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759424"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="ee5a3-102">ISymUnmanagedMethod::GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="ee5a3-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="ee5a3-103">Získá počáteční a koncové pozice dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="ee5a3-104">První pozice pole je spuštění a druhý pozice pole je do konce.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee5a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee5a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee5a3-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="ee5a3-107">[in] Počáteční a koncovou zdroje dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="ee5a3-108">[in] Počáteční a koncovou řádky do odpovídajícího zdroje dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="ee5a3-109">[in] Počáteční a koncovou sloupce do odpovídajícího zdroje dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ee5a3-110">[out] `true` pozice byl definován; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee5a3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee5a3-111">Return Value</span></span>  
 <span data-ttu-id="ee5a3-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ee5a3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee5a3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee5a3-113">Requirements</span></span>  
 <span data-ttu-id="ee5a3-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ee5a3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5a3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee5a3-115">See also</span></span>

- [<span data-ttu-id="ee5a3-116">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee5a3-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: "ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6116ee89cb643cc0010ef2c8a463fa131777584e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="3beaf-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="3beaf-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="3beaf-103">Získá spusťte nejmenší číslo řádku a největší na konci řádku pro metodu v konkrétní dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3beaf-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3beaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3beaf-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3beaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3beaf-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="3beaf-106">[v] Ukazatel na dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3beaf-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="3beaf-107">[out] Ukazatel na `ULONG32` která přijme start řádku.</span><span class="sxs-lookup"><span data-stu-id="3beaf-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="3beaf-108">[out] Ukazatel na `ULONG32` která přijme na konci řádku.</span><span class="sxs-lookup"><span data-stu-id="3beaf-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3beaf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3beaf-109">Return Value</span></span>  
 <span data-ttu-id="3beaf-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3beaf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3beaf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3beaf-111">Requirements</span></span>  
 <span data-ttu-id="3beaf-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3beaf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3beaf-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3beaf-113">See Also</span></span>  
 [<span data-ttu-id="3beaf-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3beaf-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

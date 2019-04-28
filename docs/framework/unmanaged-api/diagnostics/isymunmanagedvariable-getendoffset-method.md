---
title: ISymUnmanagedVariable::GetEndOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 325db05cc322d85e836ca9ba62b6a169e8965241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766354"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="741b0-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="741b0-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="741b0-103">Získá posun ukončení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="741b0-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="741b0-104">Pokud je to místní proměnné v rámci oboru, koncové odsazení bude spadat do posuny definované pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="741b0-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="741b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="741b0-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="741b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="741b0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="741b0-107">[out] Ukazatel `ULONG32` , která obdrží koncové odsazení.</span><span class="sxs-lookup"><span data-stu-id="741b0-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="741b0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="741b0-108">Return Value</span></span>  
 <span data-ttu-id="741b0-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="741b0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="741b0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="741b0-110">Requirements</span></span>  
 <span data-ttu-id="741b0-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="741b0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741b0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="741b0-112">See also</span></span>

- [<span data-ttu-id="741b0-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="741b0-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="741b0-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="741b0-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)

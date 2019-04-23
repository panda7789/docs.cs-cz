---
title: ISymUnmanagedMethod::GetOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223651"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="d2c10-102">ISymUnmanagedMethod::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="d2c10-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="d2c10-103">Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d2c10-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c10-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c10-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d2c10-106">[in] Ukazatel na dokument, pro kterou je požadována posun.</span><span class="sxs-lookup"><span data-stu-id="d2c10-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="d2c10-107">[in] Řádek dokumentu, pro který je vyžadován posun.</span><span class="sxs-lookup"><span data-stu-id="d2c10-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="d2c10-108">[in] Sloupec dokumentu, pro kterou je požadována posun.</span><span class="sxs-lookup"><span data-stu-id="d2c10-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d2c10-109">[out] Ukazatel `ULONG32` , která obdrží posunutí.</span><span class="sxs-lookup"><span data-stu-id="d2c10-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2c10-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c10-110">Return Value</span></span>  
 <span data-ttu-id="d2c10-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d2c10-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c10-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2c10-112">Requirements</span></span>  
 <span data-ttu-id="d2c10-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2c10-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c10-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2c10-114">See also</span></span>

- [<span data-ttu-id="d2c10-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2c10-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: "ISymUnmanagedMethod::GetOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f75236ae954b4ff3df9dd1c322cef45dfaf7fb2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="770b2-102">ISymUnmanagedMethod::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="770b2-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="770b2-103">Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="770b2-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="770b2-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="770b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="770b2-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="770b2-106">[v] Ukazatel na dokument, pro které je požadováno posun.</span><span class="sxs-lookup"><span data-stu-id="770b2-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="770b2-107">[v] Řádek dokumentu, pro který je vyžadován posun.</span><span class="sxs-lookup"><span data-stu-id="770b2-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="770b2-108">[v] Sloupec dokumentu, pro které je požadováno posun.</span><span class="sxs-lookup"><span data-stu-id="770b2-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="770b2-109">[out] Ukazatel na `ULONG32` která přijme posunutí.</span><span class="sxs-lookup"><span data-stu-id="770b2-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="770b2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="770b2-110">Return Value</span></span>  
 <span data-ttu-id="770b2-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="770b2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="770b2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="770b2-112">Requirements</span></span>  
 <span data-ttu-id="770b2-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="770b2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770b2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="770b2-114">See Also</span></span>  
 [<span data-ttu-id="770b2-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="770b2-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: ISymUnmanagedReader2::GetMethodsInDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 762649e260817c43291de416d2f1a92a8f03afb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427366"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="743d7-102">ISymUnmanagedReader2::GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="743d7-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="743d7-103">Získá každých metoda, která obsahuje informace o řádku v zadané dokumentu.</span><span class="sxs-lookup"><span data-stu-id="743d7-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="743d7-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="743d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="743d7-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="743d7-106">[v] Ukazatel na dokumentu.</span><span class="sxs-lookup"><span data-stu-id="743d7-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="743d7-107">[v] A `ULONG32` určující velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="743d7-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="743d7-108">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat metody.</span><span class="sxs-lookup"><span data-stu-id="743d7-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="743d7-109">[out] Ukazatel do vyrovnávací paměti, která přijímá metody.</span><span class="sxs-lookup"><span data-stu-id="743d7-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="743d7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="743d7-110">Return Value</span></span>  
 <span data-ttu-id="743d7-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="743d7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="743d7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="743d7-112">Requirements</span></span>  
 <span data-ttu-id="743d7-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="743d7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743d7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="743d7-114">See Also</span></span>  
 [<span data-ttu-id="743d7-115">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="743d7-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

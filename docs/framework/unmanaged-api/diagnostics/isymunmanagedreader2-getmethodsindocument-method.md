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
ms.openlocfilehash: 28b240159c36b03b2c476f56f7e6ad7b33f20649
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142339"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="785cb-102">ISymUnmanagedReader2::GetMethodsInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="785cb-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="785cb-103">Získá každou metodu, která obsahuje informace o řádek v zadané dokumentu.</span><span class="sxs-lookup"><span data-stu-id="785cb-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="785cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="785cb-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="785cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="785cb-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="785cb-106">[in] Ukazatel na dokument.</span><span class="sxs-lookup"><span data-stu-id="785cb-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="785cb-107">[in] A `ULONG32` , který označuje velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="785cb-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="785cb-108">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat metody.</span><span class="sxs-lookup"><span data-stu-id="785cb-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="785cb-109">[out] Ukazatel do vyrovnávací paměti, která přijímá metody.</span><span class="sxs-lookup"><span data-stu-id="785cb-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="785cb-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="785cb-110">Return Value</span></span>  
 <span data-ttu-id="785cb-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="785cb-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="785cb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="785cb-112">Requirements</span></span>  
 <span data-ttu-id="785cb-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="785cb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785cb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="785cb-114">See also</span></span>

- [<span data-ttu-id="785cb-115">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="785cb-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

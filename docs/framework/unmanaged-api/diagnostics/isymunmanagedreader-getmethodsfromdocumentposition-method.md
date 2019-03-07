---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15e4c9b2421b9d2cafdbabf5f9ca12d1b8b9493
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492697"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="a66e4-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="a66e4-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="a66e4-103">Vrátí pole z metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a66e4-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a66e4-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a66e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a66e4-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a66e4-106">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="a66e4-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="a66e4-107">[in] Řádku zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="a66e4-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="a66e4-108">[in] Sloupec zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="a66e4-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="a66e4-109">[in] Velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="a66e4-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="a66e4-110">[out] Ukazatel na proměnnou, která přijímá počtu prvků vrácených v `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="a66e4-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a66e4-111">[out] Pole ukazatelů, každý z nich odkazuje na [isymunmanagedmethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="a66e4-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a66e4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a66e4-112">Return Value</span></span>  
 <span data-ttu-id="a66e4-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a66e4-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a66e4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a66e4-114">Requirements</span></span>  
 <span data-ttu-id="a66e4-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a66e4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66e4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a66e4-116">See also</span></span>
- [<span data-ttu-id="a66e4-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a66e4-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

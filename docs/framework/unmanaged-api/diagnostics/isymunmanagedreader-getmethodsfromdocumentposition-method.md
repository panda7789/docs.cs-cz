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
ms.openlocfilehash: 8c84aceb0faabd879911e9595a7f3154065e2191
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426195"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="09e4b-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="09e4b-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="09e4b-103">Vrátí pole metod, z nichž každý obsahuje zarážek na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="09e4b-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09e4b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="09e4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09e4b-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="09e4b-106">[v] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="09e4b-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="09e4b-107">[v] Řádku zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="09e4b-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="09e4b-108">[v] Sloupec zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="09e4b-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="09e4b-109">[v] Velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="09e4b-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="09e4b-110">[out] Ukazatel na proměnnou, která přijímá počet elementů, vrátí se v `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="09e4b-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="09e4b-111">[out] Ukazatele, každý z nich odkazuje na pole [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který reprezentuje metodu obsahující bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="09e4b-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09e4b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09e4b-112">Return Value</span></span>  
 <span data-ttu-id="09e4b-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="09e4b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e4b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09e4b-114">Requirements</span></span>  
 <span data-ttu-id="09e4b-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09e4b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e4b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="09e4b-116">See Also</span></span>  
 [<span data-ttu-id="09e4b-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09e4b-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

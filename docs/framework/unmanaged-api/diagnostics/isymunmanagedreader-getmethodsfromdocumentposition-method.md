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
ms.openlocfilehash: 64d7f138094e03ca76ec78a50a6f37aa3d9ca2f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091730"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="506f6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="506f6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="506f6-103">Vrátí pole z metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="506f6-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="506f6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="506f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="506f6-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="506f6-106">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="506f6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="506f6-107">[in] Řádku zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="506f6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="506f6-108">[in] Sloupec zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="506f6-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="506f6-109">[in] Velikost `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="506f6-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="506f6-110">[out] Ukazatel na proměnnou, která přijímá počtu prvků vrácených v `pRetVal` pole.</span><span class="sxs-lookup"><span data-stu-id="506f6-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="506f6-111">[out] Pole ukazatelů, každý z nich odkazuje na [isymunmanagedmethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="506f6-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="506f6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="506f6-112">Return Value</span></span>  
 <span data-ttu-id="506f6-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="506f6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="506f6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="506f6-114">Requirements</span></span>  
 <span data-ttu-id="506f6-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="506f6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506f6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="506f6-116">See also</span></span>

- [<span data-ttu-id="506f6-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="506f6-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

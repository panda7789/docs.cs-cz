---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebb1a13848b1c1336287413cdd7246da748ec864
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503956"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="66e9f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="66e9f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="66e9f-103">Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="66e9f-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66e9f-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66e9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66e9f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="66e9f-106">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="66e9f-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="66e9f-107">[in] Řádku zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="66e9f-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="66e9f-108">[in] Sloupec zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="66e9f-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="66e9f-109">[out] Ukazatel na adresu [isymunmanagedmethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="66e9f-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e9f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66e9f-110">Return Value</span></span>  
 <span data-ttu-id="66e9f-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="66e9f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e9f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66e9f-112">Requirements</span></span>  
 <span data-ttu-id="66e9f-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66e9f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e9f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66e9f-114">See also</span></span>
- [<span data-ttu-id="66e9f-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66e9f-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

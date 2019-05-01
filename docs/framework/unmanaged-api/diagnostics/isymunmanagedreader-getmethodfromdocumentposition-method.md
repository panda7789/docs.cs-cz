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
ms.openlocfilehash: 4ed13397748b2668c275b221e38bd75c0dd37f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969179"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="5f3ae-102">ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="5f3ae-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="5f3ae-103">Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f3ae-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f3ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f3ae-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="5f3ae-106">[in] Zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="5f3ae-107">[in] Řádku zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="5f3ae-108">[in] Sloupec zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5f3ae-109">[out] Ukazatel na adresu [isymunmanagedmethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který představuje metodu obsahující zarážku.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f3ae-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5f3ae-110">Return Value</span></span>  
 <span data-ttu-id="5f3ae-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5f3ae-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f3ae-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f3ae-112">Requirements</span></span>  
 <span data-ttu-id="5f3ae-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5f3ae-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3ae-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f3ae-114">See also</span></span>

- [<span data-ttu-id="5f3ae-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f3ae-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

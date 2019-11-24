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
ms.openlocfilehash: 5afd48b36355835647ab8d06691f2bd2058b00cb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426732"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="216b3-102">ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="216b3-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="216b3-103">Returns the method that contains the breakpoint at the given position in a document.</span><span class="sxs-lookup"><span data-stu-id="216b3-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="216b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="216b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="216b3-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="216b3-106">[in] The specified document.</span><span class="sxs-lookup"><span data-stu-id="216b3-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="216b3-107">[in] The line of the specified document.</span><span class="sxs-lookup"><span data-stu-id="216b3-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="216b3-108">[in] The column of the specified document.</span><span class="sxs-lookup"><span data-stu-id="216b3-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="216b3-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span><span class="sxs-lookup"><span data-stu-id="216b3-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="216b3-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="216b3-110">Return Value</span></span>  
 <span data-ttu-id="216b3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="216b3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="216b3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="216b3-112">Requirements</span></span>  
 <span data-ttu-id="216b3-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="216b3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216b3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="216b3-114">See also</span></span>

- [<span data-ttu-id="216b3-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="216b3-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

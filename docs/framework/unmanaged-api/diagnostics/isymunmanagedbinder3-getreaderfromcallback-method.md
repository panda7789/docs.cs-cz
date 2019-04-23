---
title: ISymUnmanagedBinder3::GetReaderFromCallback – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9487cf89d87b5f373302dc49a08c4fabb719e746
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160755"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="c95f2-102">ISymUnmanagedBinder3::GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="c95f2-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="c95f2-103">Umožňuje uživatelům implementovat nebo zadat buď prostřednictvím zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o ladění adresáře z paměti.</span><span class="sxs-lookup"><span data-stu-id="c95f2-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c95f2-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c95f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c95f2-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="c95f2-106">[in] Ukazatel na rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="c95f2-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="c95f2-107">[in] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="c95f2-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="c95f2-108">[in] Ukazatel do cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="c95f2-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="c95f2-109">[in] Hodnota [corsymsearchpolicyattributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů.</span><span class="sxs-lookup"><span data-stu-id="c95f2-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="c95f2-110">[in] Ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c95f2-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c95f2-111">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c95f2-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c95f2-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c95f2-112">Return Value</span></span>  
 <span data-ttu-id="c95f2-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c95f2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95f2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c95f2-114">Requirements</span></span>  
 <span data-ttu-id="c95f2-115">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="c95f2-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95f2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c95f2-116">See also</span></span>

- [<span data-ttu-id="c95f2-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c95f2-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

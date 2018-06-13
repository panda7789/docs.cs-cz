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
ms.openlocfilehash: 5f44d50f6736e0698fd876eedab78dbf41434af4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426313"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="d8e8e-102">ISymUnmanagedBinder3::GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="d8e8e-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="d8e8e-103">Umožňuje uživateli implementovat nebo zadat buď přes zpětného volání `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` získat informace o directory ladění z paměti.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8e8e-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8e8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8e8e-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d8e8e-106">[v] Ukazatel rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="d8e8e-107">[v] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="d8e8e-108">[v] Ukazatel na cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="d8e8e-109">[v] Hodnota [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady, který se má použít při vyhledávání pro čtečku symbol.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="d8e8e-110">[v] Ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d8e8e-111">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8e8e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8e8e-112">Return Value</span></span>  
 <span data-ttu-id="d8e8e-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d8e8e-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8e8e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8e8e-114">Requirements</span></span>  
 <span data-ttu-id="d8e8e-115">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="d8e8e-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e8e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8e8e-116">See Also</span></span>  
 [<span data-ttu-id="d8e8e-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8e8e-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

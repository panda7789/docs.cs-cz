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
ms.openlocfilehash: a0cccc0adfc666cc8e373bc1f89c8f6f97068fde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449311"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="81053-102">ISymUnmanagedBinder3::GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="81053-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="81053-103">Umožňuje uživateli implementovat nebo doplnit pomocí zpětného volání buď `IID_IDiaReadExeAtRVACallback`, nebo `IID_IDiaReadExeAtOffsetCallback` a získat informace o ladicím adresáři z paměti.</span><span class="sxs-lookup"><span data-stu-id="81053-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81053-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81053-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81053-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81053-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="81053-106">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="81053-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="81053-107">pro Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="81053-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="81053-108">pro Ukazatel na cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="81053-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="81053-109">pro Hodnota výčtu [CorSymSearchPolicyAttributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) , která určuje zásadu, která se má použít při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="81053-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="81053-110">pro Ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="81053-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="81053-111">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="81053-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81053-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81053-112">Return Value</span></span>  
 <span data-ttu-id="81053-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="81053-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81053-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81053-114">Requirements</span></span>  
 <span data-ttu-id="81053-115">**Hlavička:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="81053-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81053-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81053-116">See also</span></span>

- [<span data-ttu-id="81053-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81053-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

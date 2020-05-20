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
ms.openlocfilehash: 4a23e9aa259f430c0d0579657952fc6aba4c307c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441653"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="54db5-102">ISymUnmanagedBinder3::GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="54db5-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="54db5-103">Umožňuje uživateli implementovat nebo dodávkovat prostřednictvím zpětného volání buď `IID_IDiaReadExeAtRVACallback` nebo `IID_IDiaReadExeAtOffsetCallback` , aby získal informace adresáře ladění z paměti.</span><span class="sxs-lookup"><span data-stu-id="54db5-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54db5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54db5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54db5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54db5-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="54db5-106">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="54db5-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="54db5-107">pro Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="54db5-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="54db5-108">pro Ukazatel na cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="54db5-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="54db5-109">pro Hodnota výčtu [CorSymSearchPolicyAttributes –](corsymsearchpolicyattributes-enumeration.md) , která určuje zásadu, která se má použít při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="54db5-109">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="54db5-110">pro Ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="54db5-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="54db5-111">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="54db5-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54db5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="54db5-112">Return Value</span></span>  
 <span data-ttu-id="54db5-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="54db5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54db5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54db5-114">Requirements</span></span>  
 <span data-ttu-id="54db5-115">**Hlavička:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="54db5-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54db5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="54db5-116">See also</span></span>

- [<span data-ttu-id="54db5-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54db5-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)

---
title: ISymUnmanagedBinder2::GetReaderForFile2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: 756ba2e71ca2e3e817a0a8b89165bb807368c1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449328"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="daf3a-102">ISymUnmanagedBinder2::GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="daf3a-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="daf3a-103">Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="daf3a-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="daf3a-104">Tato metoda poskytuje rozsáhlejší hledání souboru databáze programu (PDB) než metoda [ISymUnmanagedBinder:: GetReaderForFile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="daf3a-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf3a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daf3a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daf3a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="daf3a-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="daf3a-107">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="daf3a-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="daf3a-108">pro Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="daf3a-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="daf3a-109">pro Ukazatel na cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="daf3a-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="daf3a-110">pro Hodnota výčtu [CorSymSearchPolicyAttributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) , která určuje zásadu, která se má použít při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="daf3a-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="daf3a-111">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="daf3a-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daf3a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="daf3a-112">Return Value</span></span>  
 <span data-ttu-id="daf3a-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="daf3a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf3a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="daf3a-114">Requirements</span></span>  
 <span data-ttu-id="daf3a-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="daf3a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daf3a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="daf3a-116">Remarks</span></span>  
 <span data-ttu-id="daf3a-117">Tato verze metody může vyhledat soubor PDB v jiných oblastech než na pravé straně modulu.</span><span class="sxs-lookup"><span data-stu-id="daf3a-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="daf3a-118">Zásady hledání je možné řídit kombinací [CorSymSearchPolicyAttributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="daf3a-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="daf3a-119">`AllowReferencePathAccess | AllowSymbolServerAccess` například vyhledá soubor PDB vedle spustitelného souboru a na serveru symbolů, ale nedotazuje se do registru ani nepoužije cestu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="daf3a-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="daf3a-120">Je-li zadán parametr `searchPath`, budou tyto adresáře vždy prohledány.</span><span class="sxs-lookup"><span data-stu-id="daf3a-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf3a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daf3a-121">See also</span></span>

- [<span data-ttu-id="daf3a-122">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="daf3a-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="daf3a-123">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="daf3a-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)

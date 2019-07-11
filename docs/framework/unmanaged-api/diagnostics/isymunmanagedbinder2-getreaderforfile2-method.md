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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db917820de92b2e347385afc5217c0ca190825cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776830"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="940c5-102">ISymUnmanagedBinder2::GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="940c5-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="940c5-103">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní, které budou číst symboly ladění, které jsou spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="940c5-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="940c5-104">Tato metoda poskytuje rozsáhlejší vyhledejte soubor databáze (PDB) programu, než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="940c5-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="940c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="940c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="940c5-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="940c5-107">[in] Ukazatel na rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="940c5-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="940c5-108">[in] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="940c5-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="940c5-109">[in] Ukazatel do cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="940c5-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="940c5-110">[in] Hodnota [corsymsearchpolicyattributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady pro použití při vyhledávání pro modul pro načítání symbolů.</span><span class="sxs-lookup"><span data-stu-id="940c5-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="940c5-111">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="940c5-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="940c5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="940c5-112">Return Value</span></span>  
 <span data-ttu-id="940c5-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="940c5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="940c5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="940c5-114">Requirements</span></span>  
 <span data-ttu-id="940c5-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="940c5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="940c5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="940c5-116">Remarks</span></span>  
 <span data-ttu-id="940c5-117">Tato verze metody můžete vyhledat soubor PDB v oblastech než vpravo vedle modulu.</span><span class="sxs-lookup"><span data-stu-id="940c5-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="940c5-118">Hledání zásad se dá nastavit podle kombinace [corsymsearchpolicyattributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="940c5-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="940c5-119">Například `AllowReferencePathAccess | AllowSymbolServerAccess` hledá soubor PDB vedle spustitelný soubor a na serveru symbolů, ale ne registru nebo použijte cestu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="940c5-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="940c5-120">Pokud `searchPath` parametr zadán, budou prohledány vždy tyto adresáře.</span><span class="sxs-lookup"><span data-stu-id="940c5-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940c5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="940c5-121">See also</span></span>

- [<span data-ttu-id="940c5-122">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="940c5-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="940c5-123">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="940c5-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)

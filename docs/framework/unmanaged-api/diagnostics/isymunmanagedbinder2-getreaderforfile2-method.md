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
ms.openlocfilehash: 97b9fa537fdd9147d6d9eda036013add5393e33c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441705"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="b0ea9-102">ISymUnmanagedBinder2::GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ea9-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="b0ea9-103">Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="b0ea9-104">Tato metoda poskytuje rozsáhlejší hledání souboru databáze programu (PDB) než metoda [ISymUnmanagedBinder:: GetReaderForFile –](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b0ea9-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ea9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0ea9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ea9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0ea9-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="b0ea9-107">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b0ea9-108">pro Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b0ea9-109">pro Ukazatel na cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="b0ea9-110">pro Hodnota výčtu [CorSymSearchPolicyAttributes –](corsymsearchpolicyattributes-enumeration.md) , která určuje zásadu, která se má použít při hledání čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b0ea9-111">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b0ea9-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0ea9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0ea9-112">Return Value</span></span>  
 <span data-ttu-id="b0ea9-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ea9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0ea9-114">Requirements</span></span>  
 <span data-ttu-id="b0ea9-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b0ea9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0ea9-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0ea9-116">Remarks</span></span>  
 <span data-ttu-id="b0ea9-117">Tato verze metody může vyhledat soubor PDB v jiných oblastech než na pravé straně modulu.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="b0ea9-118">Zásady hledání je možné řídit kombinací [CorSymSearchPolicyAttributes –](corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b0ea9-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="b0ea9-119">Například `AllowReferencePathAccess | AllowSymbolServerAccess` vyhledá soubor PDB vedle spustitelného souboru a na serveru symbolů, ale nedotazuje se do registru ani nepoužije cestu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="b0ea9-120">`searchPath`Je-li zadán parametr, budou tyto adresáře vždy prohledány.</span><span class="sxs-lookup"><span data-stu-id="b0ea9-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ea9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0ea9-121">See also</span></span>

- [<span data-ttu-id="b0ea9-122">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ea9-122">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="b0ea9-123">GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ea9-123">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)

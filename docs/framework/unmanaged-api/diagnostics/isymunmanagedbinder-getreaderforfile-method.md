---
title: ISymUnmanagedBinder::GetReaderForFile – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982812"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="1fc86-102">ISymUnmanagedBinder::GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="1fc86-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="1fc86-103">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní, které budou číst symboly ladění, které jsou spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="1fc86-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="1fc86-104">Tato metoda se otevře soubor databáze (PDB) programu, pouze v případě, že je vedle spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1fc86-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="1fc86-105">Tato změna byla provedena z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="1fc86-105">This change has been made for security purposes.</span></span> <span data-ttu-id="1fc86-106">Pokud potřebujete širší vyhledejte soubor PDB, použijte [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1fc86-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc86-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fc86-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fc86-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fc86-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1fc86-109">[in] Ukazatel na rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="1fc86-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1fc86-110">[in] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="1fc86-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1fc86-111">[in] Ukazatel do cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="1fc86-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1fc86-112">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1fc86-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fc86-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1fc86-113">Return Value</span></span>  
 <span data-ttu-id="1fc86-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1fc86-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fc86-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fc86-115">Requirements</span></span>  
 <span data-ttu-id="1fc86-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1fc86-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc86-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fc86-117">See Also</span></span>  
 [<span data-ttu-id="1fc86-118">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1fc86-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="1fc86-119">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1fc86-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

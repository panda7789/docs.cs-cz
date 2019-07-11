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
ms.openlocfilehash: 6081e2dfd64625697295f2ea2d1560bc597838da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776854"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="f2c78-102">ISymUnmanagedBinder::GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="f2c78-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="f2c78-103">Rozhraní metadat a název souboru, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní, které budou číst symboly ladění, které jsou spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="f2c78-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="f2c78-104">Tato metoda se otevře soubor databáze (PDB) programu, pouze v případě, že je vedle spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f2c78-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="f2c78-105">Tato změna byla provedena z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="f2c78-105">This change has been made for security purposes.</span></span> <span data-ttu-id="f2c78-106">Pokud potřebujete širší vyhledejte soubor PDB, použijte [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f2c78-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c78-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2c78-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2c78-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2c78-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="f2c78-109">[in] Ukazatel na rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="f2c78-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="f2c78-110">[in] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c78-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="f2c78-111">[in] Ukazatel do cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="f2c78-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f2c78-112">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2c78-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2c78-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2c78-113">Return Value</span></span>  
 <span data-ttu-id="f2c78-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f2c78-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2c78-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2c78-115">Requirements</span></span>  
 <span data-ttu-id="f2c78-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f2c78-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c78-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2c78-117">See also</span></span>

- [<span data-ttu-id="f2c78-118">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2c78-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="f2c78-119">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f2c78-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

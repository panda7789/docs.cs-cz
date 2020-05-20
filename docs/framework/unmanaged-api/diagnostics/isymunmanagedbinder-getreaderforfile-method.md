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
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441731"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="6f613-102">ISymUnmanagedBinder::GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6f613-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="6f613-103">Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.</span><span class="sxs-lookup"><span data-stu-id="6f613-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="6f613-104">Tato metoda otevře soubor programové databáze (PDB) pouze v případě, že se nachází vedle spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="6f613-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="6f613-105">Tato změna byla provedena z hlediska zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6f613-105">This change has been made for security purposes.</span></span> <span data-ttu-id="6f613-106">Pokud potřebujete rozsáhlejší hledání souboru PDB, použijte metodu [ISymUnmanagedBinder2 –:: GetReaderForFile2 –](isymunmanagedbinder2-getreaderforfile2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6f613-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f613-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f613-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f613-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f613-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="6f613-109">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="6f613-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="6f613-110">pro Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="6f613-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="6f613-111">pro Ukazatel na cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="6f613-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6f613-112">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6f613-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f613-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f613-113">Return Value</span></span>  
 <span data-ttu-id="6f613-114">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6f613-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f613-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f613-115">Requirements</span></span>  
 <span data-ttu-id="6f613-116">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6f613-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f613-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f613-117">See also</span></span>

- [<span data-ttu-id="6f613-118">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f613-118">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="6f613-119">GetReaderForFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6f613-119">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)

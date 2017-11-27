---
title: "ISymUnmanagedBinder::GetReaderForFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderForFile
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 856f7eb506f77181d41ebd10148f321197ebfda3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="6a2cc-102">ISymUnmanagedBinder::GetReaderForFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6a2cc-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="6a2cc-103">Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, která budou číst související s modulem symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="6a2cc-104">Tato metoda se otevřít soubor databáze (PDB) program pouze v případě, že je vedle spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="6a2cc-105">Tato změna byla provedená z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-105">This change has been made for security purposes.</span></span> <span data-ttu-id="6a2cc-106">Pokud potřebujete rozsáhlejší vyhledejte soubor PDB, použijte [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a2cc-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a2cc-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a2cc-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="6a2cc-109">[v] Ukazatel rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="6a2cc-110">[v] Ukazatel na název souboru.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="6a2cc-111">[v] Ukazatel na cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6a2cc-112">[out] Ukazatele, který je nastavený s vráceným <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a2cc-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a2cc-113">Return Value</span></span>  
 <span data-ttu-id="6a2cc-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6a2cc-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a2cc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a2cc-115">Requirements</span></span>  
 <span data-ttu-id="6a2cc-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a2cc-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2cc-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a2cc-117">See Also</span></span>  
 [<span data-ttu-id="6a2cc-118">Isymunmanagedbinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a2cc-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="6a2cc-119">Getreaderforfile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6a2cc-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

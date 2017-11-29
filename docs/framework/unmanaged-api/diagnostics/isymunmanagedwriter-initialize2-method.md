---
title: "ISymUnmanagedWriter::Initialize2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e76543c35a717b95ae37985648986abaf16bf85d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="b7392-102">ISymUnmanagedWriter::Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b7392-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="b7392-103">Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b7392-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="b7392-104">Tato metoda také umožňuje nastavit konečného umístění souboru databáze (PDB).</span><span class="sxs-lookup"><span data-stu-id="b7392-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7392-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7392-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7392-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7392-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="b7392-107">[v] Ukazatel rozhraní vysílače metadat.</span><span class="sxs-lookup"><span data-stu-id="b7392-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="b7392-108">[v] Ukazatel na `WCHAR` obsahující název souboru, do které se zapisují symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b7392-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="b7392-109">Pokud název souboru je zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="b7392-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="b7392-110">[v] -Li zadána, zapisovač symbol vysílá symboly do danou <xref:System.Runtime.InteropServices.ComTypes.IStream> spíše než do zadaného v souboru `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="b7392-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="b7392-111">`pIStream` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="b7392-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="b7392-112">[v] `true` Pokud je to úplné opětovné sestavení; `false` Pokud je to přírůstkové kompilace.</span><span class="sxs-lookup"><span data-stu-id="b7392-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="b7392-113">[v] Ukazatel na `WCHAR` tedy řetězec cesty do konečného umístění souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="b7392-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7392-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7392-114">Return Value</span></span>  
 <span data-ttu-id="b7392-115">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b7392-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7392-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7392-116">Requirements</span></span>  
 <span data-ttu-id="b7392-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7392-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7392-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7392-118">See Also</span></span>  
 [<span data-ttu-id="b7392-119">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7392-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b7392-120">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="b7392-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

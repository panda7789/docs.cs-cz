---
title: ISymUnmanagedWriter::Initialize2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f65262a9b9850d93e934a77f154bb625a55e1e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514241"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="0bac3-102">ISymUnmanagedWriter::Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0bac3-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="0bac3-103">Nastaví rozhraní vysílače metadat, díky které bude tento zapisovač přidružené a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="0bac3-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="0bac3-104">Tato metoda také umožňuje nastavit konečné umístění souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="0bac3-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bac3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bac3-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bac3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bac3-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="0bac3-107">[in] Ukazatel na rozhraní vysílače metadat.</span><span class="sxs-lookup"><span data-stu-id="0bac3-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="0bac3-108">[in] Ukazatel `WCHAR` , který obsahuje název souboru, do kterého se zapisují symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="0bac3-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="0bac3-109">Pokud je název souboru zadaný pro zapisovače, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="0bac3-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="0bac3-110">[in] Pokud zadaná, zapisovač symbol vydává symboly do dané <xref:System.Runtime.InteropServices.ComTypes.IStream> , nikoli do souboru zadaného v `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="0bac3-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="0bac3-111">`pIStream` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="0bac3-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="0bac3-112">[in] `true` Pokud se jedná úplné opětovné sestavení; `false` Pokud přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="0bac3-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="0bac3-113">[in] Ukazatel `WCHAR` řetězec cesty, který je do konečného umístění souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="0bac3-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bac3-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bac3-114">Return Value</span></span>  
 <span data-ttu-id="0bac3-115">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0bac3-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bac3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bac3-116">Requirements</span></span>  
 <span data-ttu-id="0bac3-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0bac3-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bac3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bac3-118">See also</span></span>
- [<span data-ttu-id="0bac3-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bac3-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="0bac3-120">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="0bac3-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

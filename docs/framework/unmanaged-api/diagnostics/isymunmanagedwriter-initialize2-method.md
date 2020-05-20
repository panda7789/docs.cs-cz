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
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610064"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="3da65-102">ISymUnmanagedWriter::Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3da65-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="3da65-103">Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="3da65-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="3da65-104">Tato metoda také umožňuje nastavit konečné umístění souboru databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="3da65-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da65-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3da65-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3da65-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3da65-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="3da65-107">pro Ukazatel na rozhraní Emit metadat.</span><span class="sxs-lookup"><span data-stu-id="3da65-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="3da65-108">pro Ukazatel na `WCHAR` , který obsahuje název souboru, do kterého jsou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="3da65-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="3da65-109">Pokud je název souboru zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="3da65-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="3da65-110">pro Je-li tento parametr zadán, zapisovač symbolů vygeneruje symboly do zadaného <xref:System.Runtime.InteropServices.ComTypes.IStream> souboru, nikoli do souboru zadaného v `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="3da65-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="3da65-111">`pIStream`Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="3da65-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="3da65-112">[in] `true` Pokud se jedná o úplné opětovné sestavení; `false`Pokud se jedná o přírůstkovou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="3da65-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="3da65-113">pro Ukazatel na `WCHAR` řetězec, který je cestou k konečnému umístění souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="3da65-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3da65-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3da65-114">Return Value</span></span>  
 <span data-ttu-id="3da65-115">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3da65-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da65-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3da65-116">Requirements</span></span>  
 <span data-ttu-id="3da65-117">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3da65-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da65-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3da65-118">See also</span></span>

- [<span data-ttu-id="3da65-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3da65-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="3da65-120">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="3da65-120">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)

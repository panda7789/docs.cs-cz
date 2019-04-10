---
title: ISymUnmanagedWriter::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212047"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="d6551-102">ISymUnmanagedWriter::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="d6551-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="d6551-103">Nastaví rozhraní vysílače metadat, díky které bude tento zapisovač přidružené a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="d6551-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="d6551-104">Tuto metodu lze volat pouze jednou a musí být volána před všechny ostatní metody zapisovače.</span><span class="sxs-lookup"><span data-stu-id="d6551-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="d6551-105">Někteří uživatelé vytvářející obsah mohou vyžadovat název souboru.</span><span class="sxs-lookup"><span data-stu-id="d6551-105">Some writers may require a file name.</span></span> <span data-ttu-id="d6551-106">Název souboru však můžete vždy předat této metodě bez jakékoli negativní vliv na zapisovačů, které se nepoužívá název souboru.</span><span class="sxs-lookup"><span data-stu-id="d6551-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6551-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6551-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6551-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6551-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="d6551-109">[in] Ukazatel na rozhraní vysílače metadat.</span><span class="sxs-lookup"><span data-stu-id="d6551-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="d6551-110">[in] Název souboru, do kterého se zapisují symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="d6551-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="d6551-111">Pokud je název souboru zadaný pro zapisovače, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="d6551-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="d6551-112">[in] Je-li zadána, zapisovač symbol bude generovat symboly do dané <xref:System.Runtime.InteropServices.ComTypes.IStream> , nikoli do souboru zadaného v `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="d6551-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="d6551-113">`pIStream` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="d6551-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="d6551-114">[in] `true` Pokud se jedná úplné opětovné sestavení; `false` Pokud přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="d6551-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6551-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6551-115">Return Value</span></span>  
 <span data-ttu-id="d6551-116">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d6551-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6551-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6551-117">Requirements</span></span>  
 <span data-ttu-id="d6551-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d6551-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6551-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6551-119">See also</span></span>

- [<span data-ttu-id="d6551-120">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6551-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d6551-121">Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d6551-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

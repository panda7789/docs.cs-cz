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
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428032"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="fb305-102">ISymUnmanagedWriter::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="fb305-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="fb305-103">Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="fb305-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="fb305-104">Tuto metodu lze volat pouze jednou a musí být voláno před jiné metody zapisovače.</span><span class="sxs-lookup"><span data-stu-id="fb305-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="fb305-105">Název souboru může vyžadovat některé zapisovače.</span><span class="sxs-lookup"><span data-stu-id="fb305-105">Some writers may require a file name.</span></span> <span data-ttu-id="fb305-106">Název souboru však můžete vždy předat této metodě bez negativnímu vlivu na zapisovačů, které nepoužívají název souboru.</span><span class="sxs-lookup"><span data-stu-id="fb305-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb305-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb305-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb305-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb305-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="fb305-109">[v] Ukazatel rozhraní vysílače metadat.</span><span class="sxs-lookup"><span data-stu-id="fb305-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="fb305-110">[v] Název souboru, do které se zapisují symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="fb305-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="fb305-111">Pokud název souboru je zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="fb305-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="fb305-112">[v] -Li zadána, bude zapisovače symbol emitování symboly do danou <xref:System.Runtime.InteropServices.ComTypes.IStream> spíše než do zadaného v souboru `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="fb305-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="fb305-113">`pIStream` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="fb305-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="fb305-114">[v] `true` Pokud je to úplné opětovné sestavení; `false` Pokud je to přírůstkové kompilace.</span><span class="sxs-lookup"><span data-stu-id="fb305-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb305-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb305-115">Return Value</span></span>  
 <span data-ttu-id="fb305-116">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fb305-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb305-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb305-117">Requirements</span></span>  
 <span data-ttu-id="fb305-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb305-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb305-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb305-119">See Also</span></span>  
 [<span data-ttu-id="fb305-120">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb305-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="fb305-121">Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fb305-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

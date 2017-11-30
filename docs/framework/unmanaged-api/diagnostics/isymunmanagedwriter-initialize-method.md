---
title: "ISymUnmanagedWriter::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="7dc0a-102">ISymUnmanagedWriter::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="7dc0a-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="7dc0a-103">Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="7dc0a-104">Tuto metodu lze volat pouze jednou a musí být voláno před jiné metody zapisovače.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="7dc0a-105">Název souboru může vyžadovat některé zapisovače.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-105">Some writers may require a file name.</span></span> <span data-ttu-id="7dc0a-106">Název souboru však můžete vždy předat této metodě bez negativnímu vlivu na zapisovačů, které nepoužívají název souboru.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc0a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dc0a-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dc0a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dc0a-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="7dc0a-109">[v] Ukazatel rozhraní vysílače metadat.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="7dc0a-110">[v] Název souboru, do které se zapisují symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="7dc0a-111">Pokud název souboru je zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="7dc0a-112">[v] -Li zadána, bude zapisovače symbol emitování symboly do danou <xref:System.Runtime.InteropServices.ComTypes.IStream> spíše než do zadaného v souboru `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="7dc0a-113">`pIStream` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="7dc0a-114">[v] `true` Pokud je to úplné opětovné sestavení; `false` Pokud je to přírůstkové kompilace.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dc0a-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7dc0a-115">Return Value</span></span>  
 <span data-ttu-id="7dc0a-116">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7dc0a-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dc0a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7dc0a-117">Requirements</span></span>  
 <span data-ttu-id="7dc0a-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7dc0a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc0a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dc0a-119">See Also</span></span>  
 [<span data-ttu-id="7dc0a-120">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="7dc0a-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="7dc0a-121">Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7dc0a-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

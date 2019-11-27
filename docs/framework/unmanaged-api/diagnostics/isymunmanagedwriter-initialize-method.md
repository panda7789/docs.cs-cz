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
ms.openlocfilehash: 6e9ab623d5fe9fcfda2305df078e988a561afdc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427972"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="eb5e2-102">ISymUnmanagedWriter::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="eb5e2-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="eb5e2-103">Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="eb5e2-104">Tuto metodu lze volat pouze jednou a musí být volána před všemi jinými metodami zapisovače.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="eb5e2-105">Některé zapisovače můžou vyžadovat název souboru.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-105">Some writers may require a file name.</span></span> <span data-ttu-id="eb5e2-106">K této metodě ale můžete vždy předat název souboru bez negativního vlivu na zapisovače, které nepoužívají název souboru.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb5e2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb5e2-107">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb5e2-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb5e2-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="eb5e2-109">pro Ukazatel na rozhraní Emit metadat.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="eb5e2-110">pro Název souboru, do kterého jsou zapsány symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="eb5e2-111">Pokud je název souboru zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="eb5e2-112">pro Je-li tento parametr zadán, zapisovač symbolů bude vysílat symboly do daného <xref:System.Runtime.InteropServices.ComTypes.IStream>, nikoli do souboru zadaného v parametru `filename`.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="eb5e2-113">Parametr `pIStream` je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="eb5e2-114">[in] `true`, pokud se jedná o úplné opětovné sestavení; `false`, pokud se jedná o přírůstkovou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb5e2-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eb5e2-115">Return Value</span></span>  
 <span data-ttu-id="eb5e2-116">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="eb5e2-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb5e2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb5e2-117">Requirements</span></span>  
 <span data-ttu-id="eb5e2-118">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eb5e2-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb5e2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb5e2-119">See also</span></span>

- [<span data-ttu-id="eb5e2-120">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb5e2-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="eb5e2-121">Initialize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="eb5e2-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

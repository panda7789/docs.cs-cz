---
title: ISymUnmanagedReader::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee68533e95deb4b6efaa9226c047599f233b3954
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494753"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="cd414-102">ISymUnmanagedReader::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="cd414-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="cd414-103">Inicializuje modul pro načítání symbolů rozhraní programu pro import metadat, která tento čtecí bude spojená s, spolu s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="cd414-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd414-104">Tuto metodu lze volat pouze jednou a musí být volána před všechny ostatní metody čtečky.</span><span class="sxs-lookup"><span data-stu-id="cd414-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd414-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd414-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd414-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd414-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="cd414-107">[in] Rozhraní programu pro import metadat se kterým bude tento čtecí spojená.</span><span class="sxs-lookup"><span data-stu-id="cd414-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="cd414-108">[in] Název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="cd414-108">[in] The file name of the module.</span></span> <span data-ttu-id="cd414-109">Můžete použít `pIStream` parametr místo.</span><span class="sxs-lookup"><span data-stu-id="cd414-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="cd414-110">[in] Cesta pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="cd414-110">[in] The path to search.</span></span> <span data-ttu-id="cd414-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="cd414-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="cd414-112">[in] Soubor datového proudu, používá jako alternativu k parametr filename.</span><span class="sxs-lookup"><span data-stu-id="cd414-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd414-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd414-113">Return Value</span></span>  
 <span data-ttu-id="cd414-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cd414-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd414-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd414-115">Remarks</span></span>  
 <span data-ttu-id="cd414-116">Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí.</span><span class="sxs-lookup"><span data-stu-id="cd414-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="cd414-117">`searchPath` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="cd414-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd414-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd414-118">Requirements</span></span>  
 <span data-ttu-id="cd414-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cd414-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd414-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd414-120">See also</span></span>
- [<span data-ttu-id="cd414-121">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd414-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

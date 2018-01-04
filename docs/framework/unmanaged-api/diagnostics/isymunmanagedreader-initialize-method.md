---
title: "ISymUnmanagedReader::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="6cc89-102">ISymUnmanagedReader::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="6cc89-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="6cc89-103">Inicializuje čtečky symbol s rozhraním program pro import metadat, které bude tato čtečky spojený s, spolu s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="6cc89-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cc89-104">Tuto metodu lze volat pouze jednou a musí být volána před provedením další metody čtečky.</span><span class="sxs-lookup"><span data-stu-id="6cc89-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cc89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cc89-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cc89-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cc89-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="6cc89-107">[v] Rozhraní – Importér metadata, pomocí kterého bude tento čtečky spojený.</span><span class="sxs-lookup"><span data-stu-id="6cc89-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="6cc89-108">[v] Název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="6cc89-108">[in] The file name of the module.</span></span> <span data-ttu-id="6cc89-109">Můžete použít `pIStream` parametr místo.</span><span class="sxs-lookup"><span data-stu-id="6cc89-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="6cc89-110">[v] Cesta k vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="6cc89-110">[in] The path to search.</span></span> <span data-ttu-id="6cc89-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="6cc89-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="6cc89-112">[v] Proud souboru použít jako alternativu k parametr filename.</span><span class="sxs-lookup"><span data-stu-id="6cc89-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cc89-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6cc89-113">Return Value</span></span>  
 <span data-ttu-id="6cc89-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6cc89-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cc89-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cc89-115">Remarks</span></span>  
 <span data-ttu-id="6cc89-116">Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametry, nikoli oba dva.</span><span class="sxs-lookup"><span data-stu-id="6cc89-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="6cc89-117">`searchPath` Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="6cc89-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cc89-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cc89-118">Requirements</span></span>  
 <span data-ttu-id="6cc89-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6cc89-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc89-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cc89-120">See Also</span></span>  
 [<span data-ttu-id="6cc89-121">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cc89-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

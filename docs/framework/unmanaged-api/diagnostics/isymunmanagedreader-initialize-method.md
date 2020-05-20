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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615472"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="62897-102">ISymUnmanagedReader::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="62897-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="62897-103">Inicializuje čtečku symbolů pomocí rozhraní pro import metadat, ke kterému bude tento čtenář přidružen, společně s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="62897-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62897-104">Tuto metodu lze volat pouze jednou a je třeba ji volat před všemi jinými metodami čtenáře.</span><span class="sxs-lookup"><span data-stu-id="62897-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62897-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62897-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62897-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62897-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="62897-107">pro Rozhraní pro import metadat, ke kterému se bude tento čtenář přidružit.</span><span class="sxs-lookup"><span data-stu-id="62897-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="62897-108">pro Název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="62897-108">[in] The file name of the module.</span></span> <span data-ttu-id="62897-109">Místo toho můžete použít `pIStream` parametr.</span><span class="sxs-lookup"><span data-stu-id="62897-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="62897-110">pro Cesta, která se má vyhledat</span><span class="sxs-lookup"><span data-stu-id="62897-110">[in] The path to search.</span></span> <span data-ttu-id="62897-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="62897-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="62897-112">pro Datový proud souboru, který se používá jako alternativa k parametru filename.</span><span class="sxs-lookup"><span data-stu-id="62897-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62897-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62897-113">Return Value</span></span>  
 <span data-ttu-id="62897-114">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="62897-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62897-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62897-115">Remarks</span></span>  
 <span data-ttu-id="62897-116">Je nutné zadat pouze jeden z `filename` `pIStream` parametrů nebo, nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="62897-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="62897-117">`searchPath`Parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="62897-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62897-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62897-118">Requirements</span></span>  
 <span data-ttu-id="62897-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="62897-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62897-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="62897-120">See also</span></span>

- [<span data-ttu-id="62897-121">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62897-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

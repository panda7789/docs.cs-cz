---
title: ISymUnmanagedReader::UpdateSymbolStore – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62c954bf9d73ab564eba388e742794a330362d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080498"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="868d3-102">ISymUnmanagedReader::UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="868d3-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="868d3-103">Aktualizuje existující úložiště symbolů do úložiště symbolů delta.</span><span class="sxs-lookup"><span data-stu-id="868d3-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="868d3-104">Tato metoda se používá ve scénářích edit-and-continue aktualizovat úložiště symbolů tak, aby odpovídaly rozdíly do původní přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="868d3-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="868d3-105">Je nutné zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí.</span><span class="sxs-lookup"><span data-stu-id="868d3-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="868d3-106">Pokud `filename` není zadán, aktualizuje úložiště symbolů se symboly v daném souboru.</span><span class="sxs-lookup"><span data-stu-id="868d3-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="868d3-107">Pokud `pIStream` není zadána, úložiště se aktualizuje s daty z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="868d3-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868d3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="868d3-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="868d3-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="868d3-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="868d3-110">[in] Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="868d3-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="868d3-111">[in] Datový proud souboru použít jako alternativu k `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="868d3-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="868d3-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="868d3-112">Return Value</span></span>  
 <span data-ttu-id="868d3-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="868d3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="868d3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="868d3-114">Requirements</span></span>  
 <span data-ttu-id="868d3-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="868d3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868d3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="868d3-116">See also</span></span>

- [<span data-ttu-id="868d3-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="868d3-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

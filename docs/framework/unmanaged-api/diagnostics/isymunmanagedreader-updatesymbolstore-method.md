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
ms.openlocfilehash: 81f9db872e9904d2297221e266be710837d0fb66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427379"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="7d499-102">ISymUnmanagedReader::UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="7d499-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="7d499-103">Aktualizuje existující úložiště symbolů s úložištěm symbol delta.</span><span class="sxs-lookup"><span data-stu-id="7d499-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="7d499-104">Tato metoda se používá ve scénářích upravit a pokračovat se aktualizovat úložiště symbolů tak, aby odpovídaly rozdílů na původní přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="7d499-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d499-105">Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametry, nikoli oba dva.</span><span class="sxs-lookup"><span data-stu-id="7d499-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="7d499-106">Pokud `filename` je zadán, bude úložiště symbolů aktualizována symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="7d499-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="7d499-107">Pokud `pIStream` je zadaný úložiště se aktualizuje pomocí data z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="7d499-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d499-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d499-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d499-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d499-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="7d499-110">[v] Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="7d499-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="7d499-111">[v] Datový proud souboru, používá jako alternativu k `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="7d499-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d499-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d499-112">Return Value</span></span>  
 <span data-ttu-id="7d499-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7d499-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d499-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d499-114">Requirements</span></span>  
 <span data-ttu-id="7d499-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7d499-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d499-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d499-116">See Also</span></span>  
 [<span data-ttu-id="7d499-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d499-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

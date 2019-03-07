---
title: ISymUnmanagedReader::ReplaceSymbolStore – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b863816bfb7ed1a5db1fa2234db224b01cb6c9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481544"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="f54e8-102">ISymUnmanagedReader::ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="f54e8-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="f54e8-103">Nahradí existující úložiště symbolů do úložiště symbolů delta.</span><span class="sxs-lookup"><span data-stu-id="f54e8-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="f54e8-104">Tato metoda je podobný [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody, s tím rozdílem, že daný delta funguje jako o úplné nahrazení spíše než aktualizace.</span><span class="sxs-lookup"><span data-stu-id="f54e8-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f54e8-105">Je nutné zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí.</span><span class="sxs-lookup"><span data-stu-id="f54e8-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="f54e8-106">Pokud `filename` není zadán, aktualizuje úložiště symbolů se symboly v daném souboru.</span><span class="sxs-lookup"><span data-stu-id="f54e8-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="f54e8-107">Pokud `pIStream` není zadána, úložiště se aktualizuje s daty z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="f54e8-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f54e8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f54e8-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f54e8-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="f54e8-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f54e8-110">[in] Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="f54e8-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="f54e8-111">[in] Datový proud souboru použít jako alternativu k `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="f54e8-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f54e8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f54e8-112">Return Value</span></span>  
 <span data-ttu-id="f54e8-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f54e8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f54e8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f54e8-114">Requirements</span></span>  
 <span data-ttu-id="f54e8-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f54e8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54e8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f54e8-116">See also</span></span>
- [<span data-ttu-id="f54e8-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f54e8-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

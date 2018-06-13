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
ms.openlocfilehash: 03607cf96d73e96eef63fe62b86b50be02f34421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428199"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="5a7a4-102">ISymUnmanagedReader::ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="5a7a4-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="5a7a4-103">Nahradí existující úložiště symbolů s úložištěm symbol delta.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="5a7a4-104">Tato metoda je podobná [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metoda, s tím rozdílem, že daný delta funguje jako o úplné nahrazení spíše než aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a7a4-105">Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametry, nikoli oba dva.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="5a7a4-106">Pokud `filename` je zadán, bude úložiště symbolů aktualizována symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="5a7a4-107">Pokud `pIStream` je zadaný úložiště se aktualizuje pomocí data z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a7a4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a7a4-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a7a4-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a7a4-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="5a7a4-110">[v] Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="5a7a4-111">[v] Datový proud souboru, používá jako alternativu k `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a7a4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a7a4-112">Return Value</span></span>  
 <span data-ttu-id="5a7a4-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5a7a4-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a7a4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a7a4-114">Requirements</span></span>  
 <span data-ttu-id="5a7a4-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a7a4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a7a4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a7a4-116">See Also</span></span>  
 [<span data-ttu-id="5a7a4-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a7a4-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

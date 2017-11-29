---
title: "ISymUnmanagedReader::ReplaceSymbolStore – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.ReplaceSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09bcad4898cf4d3310a96164bdc82006e185006f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="3fb36-102">ISymUnmanagedReader::ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="3fb36-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="3fb36-103">Nahradí existující úložiště symbolů s úložištěm symbol delta.</span><span class="sxs-lookup"><span data-stu-id="3fb36-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="3fb36-104">Tato metoda je podobná [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metoda, s tím rozdílem, že daný delta funguje jako o úplné nahrazení spíše než aktualizace.</span><span class="sxs-lookup"><span data-stu-id="3fb36-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fb36-105">Je třeba zadat pouze jeden z `filename` nebo `pIStream` parametry, nikoli oba dva.</span><span class="sxs-lookup"><span data-stu-id="3fb36-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="3fb36-106">Pokud `filename` je zadán, bude úložiště symbolů aktualizována symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="3fb36-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="3fb36-107">Pokud `pIStream` je zadaný úložiště se aktualizuje pomocí data z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="3fb36-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb36-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb36-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fb36-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fb36-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="3fb36-110">[v] Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="3fb36-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="3fb36-111">[v] Datový proud souboru, používá jako alternativu k `filename` parametr.</span><span class="sxs-lookup"><span data-stu-id="3fb36-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fb36-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3fb36-112">Return Value</span></span>  
 <span data-ttu-id="3fb36-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3fb36-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb36-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fb36-114">Requirements</span></span>  
 <span data-ttu-id="3fb36-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3fb36-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb36-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb36-116">See Also</span></span>  
 [<span data-ttu-id="3fb36-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fb36-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

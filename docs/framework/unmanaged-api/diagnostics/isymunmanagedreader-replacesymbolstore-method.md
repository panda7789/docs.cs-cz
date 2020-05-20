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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615446"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="9163a-102">ISymUnmanagedReader::ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="9163a-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="9163a-103">Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů.</span><span class="sxs-lookup"><span data-stu-id="9163a-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="9163a-104">Tato metoda je podobná metodě [UpdateSymbolStore –](isymunmanagedreader-updatesymbolstore-method.md) , s tím rozdílem, že daný rozdíl funguje jako kompletní náhrada, nikoli jako aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9163a-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9163a-105">Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="9163a-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="9163a-106">`filename`Je-li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="9163a-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="9163a-107">`pIStream`Je-li parametr zadán, bude úložiště Aktualizováno daty z <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="9163a-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9163a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9163a-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9163a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="9163a-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="9163a-110">pro Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="9163a-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="9163a-111">pro Datový proud souboru, který se používá jako alternativa k `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="9163a-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9163a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9163a-112">Return Value</span></span>  
 <span data-ttu-id="9163a-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9163a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9163a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9163a-114">Requirements</span></span>  
 <span data-ttu-id="9163a-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9163a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9163a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9163a-116">See also</span></span>

- [<span data-ttu-id="9163a-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9163a-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

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
ms.openlocfilehash: ccc787aa1c820a486d9a513055c9c9834b90bd1a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615433"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="dbbe2-102">ISymUnmanagedReader::UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="dbbe2-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="dbbe2-103">Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="dbbe2-104">Tato metoda se používá ve scénářích pro úpravy a pokračování k aktualizaci úložiště symbolů tak, aby odpovídaly rozdílům v původním přenositelném spustitelném souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="dbbe2-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbbe2-105">Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="dbbe2-106">`filename`Je-li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="dbbe2-107">`pIStream`Je-li parametr zadán, bude úložiště Aktualizováno daty z <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="dbbe2-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbe2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbbe2-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbbe2-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbbe2-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="dbbe2-110">pro Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="dbbe2-111">pro Datový proud souboru, který se používá jako alternativa k `filename` parametru.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbbe2-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dbbe2-112">Return Value</span></span>  
 <span data-ttu-id="dbbe2-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="dbbe2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbe2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbbe2-114">Requirements</span></span>  
 <span data-ttu-id="dbbe2-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dbbe2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbe2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbbe2-116">See also</span></span>

- [<span data-ttu-id="dbbe2-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbbe2-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

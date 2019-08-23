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
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939010"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="cac44-102">ISymUnmanagedReader::UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="cac44-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="cac44-103">Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="cac44-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="cac44-104">Tato metoda se používá ve scénářích pro úpravy a pokračování k aktualizaci úložiště symbolů tak, aby odpovídaly rozdílům v původním přenositelném spustitelném souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="cac44-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cac44-105">Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="cac44-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="cac44-106">Je `filename` -li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="cac44-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="cac44-107">Je `pIStream` -li parametr zadán, bude úložiště Aktualizováno daty <xref:System.Runtime.InteropServices.ComTypes.IStream>z.</span><span class="sxs-lookup"><span data-stu-id="cac44-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac44-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cac44-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cac44-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="cac44-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="cac44-110">pro Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="cac44-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="cac44-111">pro Datový proud souboru, který se používá jako alternativa `filename` k parametru.</span><span class="sxs-lookup"><span data-stu-id="cac44-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cac44-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cac44-112">Return Value</span></span>  
 <span data-ttu-id="cac44-113">S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cac44-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac44-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cac44-114">Requirements</span></span>  
 <span data-ttu-id="cac44-115">**Hlaviček** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cac44-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac44-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cac44-116">See also</span></span>

- [<span data-ttu-id="cac44-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cac44-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

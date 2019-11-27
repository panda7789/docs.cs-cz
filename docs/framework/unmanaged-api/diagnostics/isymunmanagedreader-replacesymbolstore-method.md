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
ms.openlocfilehash: 60c3537a80c39f758f46e6f2f0a5f2bcd27350b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445731"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="06e09-102">ISymUnmanagedReader::ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="06e09-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="06e09-103">Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů.</span><span class="sxs-lookup"><span data-stu-id="06e09-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="06e09-104">Tato metoda je podobná metodě [UpdateSymbolStore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) , s tím rozdílem, že daný rozdíl funguje jako kompletní náhrada, nikoli jako aktualizace.</span><span class="sxs-lookup"><span data-stu-id="06e09-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06e09-105">Je nutné zadat pouze jeden z parametrů `filename` nebo `pIStream`, nikoli obojí.</span><span class="sxs-lookup"><span data-stu-id="06e09-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="06e09-106">Je-li zadán `filename`, bude úložiště symbolů Aktualizováno symboly v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="06e09-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="06e09-107">Je-li zadán `pIStream`, bude úložiště Aktualizováno daty z <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="06e09-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e09-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e09-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06e09-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="06e09-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="06e09-110">pro Název souboru, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="06e09-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="06e09-111">pro Datový proud souboru, který se používá jako alternativa k parametru `filename`.</span><span class="sxs-lookup"><span data-stu-id="06e09-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06e09-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06e09-112">Return Value</span></span>  
 <span data-ttu-id="06e09-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="06e09-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e09-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06e09-114">Requirements</span></span>  
 <span data-ttu-id="06e09-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="06e09-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e09-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06e09-116">See also</span></span>

- [<span data-ttu-id="06e09-117">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06e09-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

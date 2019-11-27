---
title: ISymUnmanagedReader::GetSymbolStoreFileName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: b3674c4058dba2f6185418b55b35eefb14c312f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431236"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="6ca30-102">ISymUnmanagedReader::GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="6ca30-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="6ca30-103">Poskytuje název souboru na disku pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="6ca30-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ca30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ca30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ca30-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6ca30-106">pro Velikost vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="6ca30-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6ca30-107">mimo Ukazatel na proměnnou, která přijímá délku názvu vráceného v `szName`, včetně ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="6ca30-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="6ca30-108">mimo Ukazatel na proměnnou, která přijímá název souboru úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="6ca30-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ca30-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ca30-109">Return Value</span></span>  
 <span data-ttu-id="6ca30-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6ca30-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ca30-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ca30-111">Requirements</span></span>  
 <span data-ttu-id="6ca30-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6ca30-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca30-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ca30-113">See also</span></span>

- [<span data-ttu-id="6ca30-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ca30-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

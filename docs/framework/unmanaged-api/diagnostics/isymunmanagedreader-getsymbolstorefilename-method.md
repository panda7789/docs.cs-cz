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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 147b33a3f49f9163daea776779ca26f62561a84e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170375"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="249a6-102">ISymUnmanagedReader::GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="249a6-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="249a6-103">Poskytuje název souboru na disku úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="249a6-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="249a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="249a6-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="249a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="249a6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="249a6-106">[in] Velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="249a6-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="249a6-107">[out] Ukazatel na proměnnou, která přijímá délka názvu vrátil v `szName`, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="249a6-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="249a6-108">[out] Ukazatel na proměnnou, která přijímá název souboru v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="249a6-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="249a6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="249a6-109">Return Value</span></span>  
 <span data-ttu-id="249a6-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="249a6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="249a6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="249a6-111">Requirements</span></span>  
 <span data-ttu-id="249a6-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="249a6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="249a6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="249a6-113">See also</span></span>

- [<span data-ttu-id="249a6-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="249a6-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

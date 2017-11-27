---
title: "ISymUnmanagedReader::GetSymbolStoreFileName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymbolStoreFileName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 951dfd45f6b313b6cde28f3f65f2799380a33a78
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="3396f-102">ISymUnmanagedReader::GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="3396f-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="3396f-103">Obsahuje název souboru na disku úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="3396f-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3396f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3396f-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3396f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3396f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3396f-106">[v] Velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3396f-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3396f-107">[out] Ukazatel na proměnnou, která přijímá délka názvu, vrátí se v `szName`, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3396f-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3396f-108">[out] Ukazatel na proměnnou, která přijímá název souboru úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="3396f-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3396f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3396f-109">Return Value</span></span>  
 <span data-ttu-id="3396f-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3396f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3396f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3396f-111">Requirements</span></span>  
 <span data-ttu-id="3396f-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3396f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3396f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3396f-113">See Also</span></span>  
 [<span data-ttu-id="3396f-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3396f-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

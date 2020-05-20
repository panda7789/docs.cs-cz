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
ms.openlocfilehash: 6ffab3b2f81680404f870cfd63ae5125173a346c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615511"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="56f9e-102">ISymUnmanagedReader::GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="56f9e-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="56f9e-103">Poskytuje název souboru na disku pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="56f9e-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56f9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56f9e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="56f9e-106">pro Velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="56f9e-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="56f9e-107">mimo Ukazatel na proměnnou, která přijímá délku názvu vráceného v `szName` , včetně ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="56f9e-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="56f9e-108">mimo Ukazatel na proměnnou, která přijímá název souboru úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="56f9e-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56f9e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56f9e-109">Return Value</span></span>  
 <span data-ttu-id="56f9e-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="56f9e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f9e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f9e-111">Requirements</span></span>  
 <span data-ttu-id="56f9e-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="56f9e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f9e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="56f9e-113">See also</span></span>

- [<span data-ttu-id="56f9e-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56f9e-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)

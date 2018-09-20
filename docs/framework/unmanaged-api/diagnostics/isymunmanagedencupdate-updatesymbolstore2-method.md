---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78d9e27299c9d7ed7d6cb9b09dd659ba081c5fde
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320354"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="16860-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="16860-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="16860-103">Umožňuje kompilátoru chcete vynechat, nechte funkce, které nebyly upraveny z datového proudu databáze (PDB) programu, pokud informace o řádku splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="16860-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="16860-104">Informace o správné řádku se dá určit pomocí staré informace o řádku PDB a jeden rozdílové hodnoty všech řádků ve funkci.</span><span class="sxs-lookup"><span data-stu-id="16860-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16860-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16860-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16860-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16860-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="16860-107">[in] Ukazatel [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , který obsahuje informace o řádku.</span><span class="sxs-lookup"><span data-stu-id="16860-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="16860-108">[in] Ukazatel [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) struktura obsahující řádky, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="16860-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="16860-109">[in] A `ULONG` , který představuje počet řádků, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="16860-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16860-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="16860-110">Return Value</span></span>  
 <span data-ttu-id="16860-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="16860-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16860-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16860-112">Requirements</span></span>  
 <span data-ttu-id="16860-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16860-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16860-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="16860-114">See Also</span></span>  
 [<span data-ttu-id="16860-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16860-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

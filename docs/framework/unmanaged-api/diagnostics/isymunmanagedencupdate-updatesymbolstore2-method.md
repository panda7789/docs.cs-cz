---
title: "ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a366047530f3433ab1bfbb5f30d4b9b54c5bdb08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="b5b92-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b5b92-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="b5b92-103">Umožňuje kompilátoru vynechat funkce, které nebyly upraveny z datového proudu program databáze (PDB), zadaný informace řádku splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="b5b92-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="b5b92-104">Informace o správné řádku se dá určit pomocí staré informace řádku PDB a jeden rozdílové u všech spojnic ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b5b92-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b92-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5b92-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5b92-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5b92-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="b5b92-107">[v] Ukazatel na <xref:IStream> obsahující informace o řádku.</span><span class="sxs-lookup"><span data-stu-id="b5b92-107">[in] A pointer to an <xref:IStream> that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="b5b92-108">[v] Ukazatel [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) struktura obsahující řádky, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="b5b92-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="b5b92-109">[v] A `ULONG` představující počet řádků, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="b5b92-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5b92-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5b92-110">Return Value</span></span>  
 <span data-ttu-id="b5b92-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b5b92-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5b92-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5b92-112">Requirements</span></span>  
 <span data-ttu-id="b5b92-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5b92-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b92-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5b92-114">See Also</span></span>  
 [<span data-ttu-id="b5b92-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5b92-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

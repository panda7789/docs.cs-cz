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
ms.openlocfilehash: 393984241412f543b6ac082484cf5e23edb2d9f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448978"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="1e83a-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1e83a-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="1e83a-103">Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database), za předpokladu, že informace o řádku splňují požadavky.</span><span class="sxs-lookup"><span data-stu-id="1e83a-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="1e83a-104">Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1e83a-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e83a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e83a-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e83a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e83a-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="1e83a-107">pro Ukazatel na [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , který obsahuje informace o řádku.</span><span class="sxs-lookup"><span data-stu-id="1e83a-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="1e83a-108">pro Ukazatel na strukturu [symlinedelta –](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) , která obsahuje řádky, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="1e83a-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="1e83a-109">pro `ULONG`, která představuje počet řádků, které byly změněny.</span><span class="sxs-lookup"><span data-stu-id="1e83a-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e83a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1e83a-110">Return Value</span></span>  
 <span data-ttu-id="1e83a-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1e83a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e83a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e83a-112">Requirements</span></span>  
 <span data-ttu-id="1e83a-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1e83a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e83a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e83a-114">See also</span></span>

- [<span data-ttu-id="1e83a-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e83a-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

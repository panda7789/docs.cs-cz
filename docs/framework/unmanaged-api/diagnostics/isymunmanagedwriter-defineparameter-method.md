---
title: ISymUnmanagedWriter::DefineParameter – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: bc1b65de026a674a3dff183050a5a205fd7052c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428005"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="e7f65-102">ISymUnmanagedWriter::DefineParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="e7f65-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="e7f65-103">Definuje jeden parametr v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="e7f65-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="e7f65-104">Typ parametru je přijímán z pozice parametru (Sequence) v rámci signatury metody.</span><span class="sxs-lookup"><span data-stu-id="e7f65-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="e7f65-105">Pokud jsou parametry definovány v metadatech pro danou metodu, nemusíte je znovu definovat pomocí této metody.</span><span class="sxs-lookup"><span data-stu-id="e7f65-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="e7f65-106">Čtečky symbolů musí před kontrolou úložiště symbolů zkontrolovat běžná metadata pro parametry.</span><span class="sxs-lookup"><span data-stu-id="e7f65-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f65-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7f65-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7f65-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7f65-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e7f65-109">pro Název parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f65-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="e7f65-110">pro Atributy parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f65-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="e7f65-111">pro Signatura parametru</span><span class="sxs-lookup"><span data-stu-id="e7f65-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="e7f65-112">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="e7f65-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="e7f65-113">pro První adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f65-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="e7f65-114">pro Druhá adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f65-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="e7f65-115">pro Třetí adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="e7f65-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7f65-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7f65-116">Return Value</span></span>  
 <span data-ttu-id="e7f65-117">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e7f65-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f65-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7f65-118">Requirements</span></span>  
 <span data-ttu-id="e7f65-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e7f65-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f65-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7f65-120">See also</span></span>

- [<span data-ttu-id="e7f65-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7f65-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

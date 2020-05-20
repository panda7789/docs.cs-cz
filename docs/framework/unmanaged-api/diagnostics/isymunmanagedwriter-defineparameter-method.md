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
ms.openlocfilehash: c695aa80ea3bf90a29ce7c5d11eda7fae5fe7b2d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614809"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="1d827-102">ISymUnmanagedWriter::DefineParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="1d827-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="1d827-103">Definuje jeden parametr v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="1d827-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="1d827-104">Typ parametru je přijímán z pozice parametru (Sequence) v rámci signatury metody.</span><span class="sxs-lookup"><span data-stu-id="1d827-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="1d827-105">Pokud jsou parametry definovány v metadatech pro danou metodu, nemusíte je znovu definovat pomocí této metody.</span><span class="sxs-lookup"><span data-stu-id="1d827-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="1d827-106">Čtečky symbolů musí před kontrolou úložiště symbolů zkontrolovat běžná metadata pro parametry.</span><span class="sxs-lookup"><span data-stu-id="1d827-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d827-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d827-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1d827-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d827-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1d827-109">pro Název parametru.</span><span class="sxs-lookup"><span data-stu-id="1d827-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1d827-110">pro Atributy parametru.</span><span class="sxs-lookup"><span data-stu-id="1d827-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="1d827-111">pro Signatura parametru</span><span class="sxs-lookup"><span data-stu-id="1d827-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1d827-112">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="1d827-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1d827-113">pro První adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="1d827-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1d827-114">pro Druhá adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="1d827-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1d827-115">pro Třetí adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="1d827-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d827-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1d827-116">Return Value</span></span>  
 <span data-ttu-id="1d827-117">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1d827-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d827-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d827-118">Requirements</span></span>  
 <span data-ttu-id="1d827-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1d827-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d827-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d827-120">See also</span></span>

- [<span data-ttu-id="1d827-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d827-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

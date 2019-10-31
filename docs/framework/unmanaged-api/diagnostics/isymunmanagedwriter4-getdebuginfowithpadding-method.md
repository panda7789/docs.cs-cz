---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121658"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="e9cf5-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="e9cf5-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="e9cf5-103">Funguje stejně jako [Metoda GetDebugInfo –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněn nulami za ukončovacím znakem null, aby data řetězce měla pevnou velikost `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e9cf5-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="e9cf5-104">Odsazení je zadáno pouze v případě, že délka řetězce cesty je menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="e9cf5-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="e9cf5-105">To usnadňuje psaní nástrojů, které rozdílují soubory PE.</span><span class="sxs-lookup"><span data-stu-id="e9cf5-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9cf5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9cf5-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9cf5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9cf5-107">Parameters</span></span>  
  
|<span data-ttu-id="e9cf5-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="e9cf5-108">Parameter</span></span>|<span data-ttu-id="e9cf5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e9cf5-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="e9cf5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9cf5-110">Return Value</span></span>  
 <span data-ttu-id="e9cf5-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e9cf5-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9cf5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9cf5-112">Requirements</span></span>  
 <span data-ttu-id="e9cf5-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e9cf5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cf5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9cf5-114">See also</span></span>

- [<span data-ttu-id="e9cf5-115">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9cf5-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)

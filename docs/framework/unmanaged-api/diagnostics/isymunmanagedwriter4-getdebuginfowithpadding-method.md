---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: cfc6c22558cee780823c8cca0c36b883147e9496
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614640"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="2f073-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="2f073-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="2f073-103">Funguje stejně jako [Metoda GetDebugInfo –](isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněn nulami za ukončovacím znakem null, aby data řetězce měla pevnou velikost `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2f073-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="2f073-104">Odsazení je zadáno pouze v případě, že délka řetězce cesty je menší než `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2f073-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="2f073-105">To usnadňuje psaní nástrojů, které rozdílují soubory PE.</span><span class="sxs-lookup"><span data-stu-id="2f073-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f073-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f073-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f073-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f073-107">Parameters</span></span>  
  
|<span data-ttu-id="2f073-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="2f073-108">Parameter</span></span>|<span data-ttu-id="2f073-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f073-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="2f073-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f073-110">Return Value</span></span>  
 <span data-ttu-id="2f073-111">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2f073-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f073-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f073-112">Requirements</span></span>  
 <span data-ttu-id="2f073-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f073-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f073-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f073-114">See also</span></span>

- [<span data-ttu-id="2f073-115">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f073-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)

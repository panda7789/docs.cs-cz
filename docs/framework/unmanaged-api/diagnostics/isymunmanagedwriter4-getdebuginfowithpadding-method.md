---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a703c7c8adf5d770ea74f8ed869568978f3b42f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428622"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="c166a-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="c166a-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="c166a-103">Funguje stejně jako [getdebuginfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněno nulami následující ukončující znak hodnoty null tak, aby data řetězec pevnou velikost `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="c166a-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="c166a-104">Odsazení je poskytnuta pouze v případě délka řetězce cesty, samotné je menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="c166a-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="c166a-105">To usnadňuje vytvoření nástrojů pro tento rozdíl PE soubory.</span><span class="sxs-lookup"><span data-stu-id="c166a-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c166a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c166a-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c166a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c166a-107">Parameters</span></span>  
  
|<span data-ttu-id="c166a-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="c166a-108">Parameter</span></span>|<span data-ttu-id="c166a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c166a-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="c166a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c166a-110">Return Value</span></span>  
 <span data-ttu-id="c166a-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c166a-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c166a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c166a-112">Requirements</span></span>  
 <span data-ttu-id="c166a-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c166a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c166a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c166a-114">See Also</span></span>  
 [<span data-ttu-id="c166a-115">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c166a-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)

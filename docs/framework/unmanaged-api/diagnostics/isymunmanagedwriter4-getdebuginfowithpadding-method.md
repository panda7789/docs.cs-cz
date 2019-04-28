---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 191aa16c285b3a28beed65004d65525c9214ec93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650736"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="29cee-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="29cee-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="29cee-103">Funguje stejně jako [GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty doplněno nulami po ukončujícího znaku null na pevnou velikost, aby se data řetězce `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="29cee-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="29cee-104">Odsazení je uveden pouze pokud je délka řetězec cesty, samotný menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="29cee-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="29cee-105">Díky tomu je snazší psát nástroje tento rozdíl PE soubory.</span><span class="sxs-lookup"><span data-stu-id="29cee-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29cee-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29cee-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="29cee-107">Parameters</span></span>  
  
|<span data-ttu-id="29cee-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="29cee-108">Parameter</span></span>|<span data-ttu-id="29cee-109">Popis</span><span class="sxs-lookup"><span data-stu-id="29cee-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="29cee-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29cee-110">Return Value</span></span>  
 <span data-ttu-id="29cee-111">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="29cee-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29cee-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29cee-112">Requirements</span></span>  
 <span data-ttu-id="29cee-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29cee-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cee-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29cee-114">See also</span></span>

- [<span data-ttu-id="29cee-115">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29cee-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)

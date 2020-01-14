---
title: GetTypeLibInfo – funkce
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: 4f05eb2e6ef31cf1993a623c38bb177f7e3c297e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935654"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="692f9-102">GetTypeLibInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="692f9-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="692f9-103">Vrátí informace o zadané knihovně typů prozkoumáním její struktury [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="692f9-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="692f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="692f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="692f9-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="692f9-106">pro Název souboru knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="692f9-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="692f9-107">mimo Identifikátor GUID knihovny typů</span><span class="sxs-lookup"><span data-stu-id="692f9-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="692f9-108">mimo ID lokalizace knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="692f9-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="692f9-109">mimo Příznak [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) , který identifikuje cílový operační systém pro knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="692f9-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="692f9-110">Běžné hodnoty jsou SYS_WIN32 a SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="692f9-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="692f9-111">mimo Hlavní číslo verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="692f9-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="692f9-112">Například pro verzi *x. y*je hlavní číslo verze *x*.</span><span class="sxs-lookup"><span data-stu-id="692f9-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="692f9-113">mimo Číslo dílčí verze knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="692f9-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="692f9-114">Například pro verzi *x. y*je číslo dílčí verze *y*.</span><span class="sxs-lookup"><span data-stu-id="692f9-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="692f9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="692f9-115">Remarks</span></span>  
 <span data-ttu-id="692f9-116">Funkce `GetTypeLibInfo` je volána nástrojem [Tlbexp. exe (Exportér knihovny typů)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="692f9-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="692f9-117">Tento nástroj generuje knihovnu typů, která popisuje typy v sestavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="692f9-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="692f9-118">Pokud je libovolný parametr null, funkce vrátí `HRESULT` `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="692f9-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="692f9-119">V opačném případě vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="692f9-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="692f9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="692f9-120">Requirements</span></span>  
 <span data-ttu-id="692f9-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="692f9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="692f9-122">**Hlavička:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="692f9-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="692f9-123">**Knihovna:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="692f9-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="692f9-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="692f9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692f9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="692f9-125">See also</span></span>

- [<span data-ttu-id="692f9-126">Podpůrné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="692f9-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="692f9-127">LoadTypeLibEx – funkce</span><span class="sxs-lookup"><span data-stu-id="692f9-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)

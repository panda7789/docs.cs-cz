---
title: LoadLibraryShim – funkce
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 1759ee2ecf08322b745a4f80a62b24596c4504cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123254"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="5903a-102">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="5903a-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="5903a-103">Načte zadanou verzi knihovny DLL, která je součástí .NET Framework Distribuovatelný balíček.</span><span class="sxs-lookup"><span data-stu-id="5903a-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="5903a-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5903a-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="5903a-105">Místo toho použijte metodu [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5903a-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5903a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5903a-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5903a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5903a-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="5903a-108">pro Řetězec zakončený nulou, který představuje název knihovny DLL, která má být načtena z knihovny .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5903a-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="5903a-109">pro Řetězec zakončený nulou, který představuje verzi knihovny DLL, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="5903a-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="5903a-110">Pokud je `szVersion` null, verze vybraná pro načtení je nejnovější verze zadané knihovny DLL, která je menší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="5903a-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="5903a-111">To znamená, že všechny verze, které jsou větší nebo rovny verzi 4, jsou ignorovány, pokud je `szVersion` null a není-li nainstalována žádná verze, která je nižší než verze 4, knihovna DLL se nemůže načíst.</span><span class="sxs-lookup"><span data-stu-id="5903a-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="5903a-112">K tomu je potřeba zajistit, aby instalace .NET Framework 4 neovlivnila stávající aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="5903a-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="5903a-113">Podívejte se na záznam [v rámci proc SxS a migrace rychlé zprovoznění](https://go.microsoft.com/fwlink/?LinkId=200329) na blogu týmu CLR.</span><span class="sxs-lookup"><span data-stu-id="5903a-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5903a-114">Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="5903a-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="5903a-115">mimo Ukazatel na popisovač modulu.</span><span class="sxs-lookup"><span data-stu-id="5903a-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5903a-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5903a-116">Return Value</span></span>  
 <span data-ttu-id="5903a-117">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="5903a-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5903a-118">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="5903a-118">Return code</span></span>|<span data-ttu-id="5903a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5903a-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5903a-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="5903a-120">S_OK</span></span>|<span data-ttu-id="5903a-121">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5903a-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="5903a-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="5903a-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="5903a-123">Načítání `szDllName` vyžaduje načtení modulu CLR (Common Language Runtime) a potřebnou verzi modulu CLR nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="5903a-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5903a-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5903a-124">Remarks</span></span>  
 <span data-ttu-id="5903a-125">Tato funkce se používá k načtení knihoven DLL, které jsou součástí .NET Framework Distribuovatelný balíček.</span><span class="sxs-lookup"><span data-stu-id="5903a-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="5903a-126">Nenačítá uživatelem generované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5903a-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5903a-127">Počínaje verzí 2,0 .NET Framework, načtení souboru Fusion. dll způsobí načtení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5903a-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="5903a-128">Důvodem je, že funkce v Fusion. dll jsou nyní obálky, jejichž implementace jsou poskytovány modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="5903a-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5903a-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5903a-129">Requirements</span></span>  
 <span data-ttu-id="5903a-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5903a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5903a-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5903a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5903a-132">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5903a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5903a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5903a-133">See also</span></span>

- [<span data-ttu-id="5903a-134">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="5903a-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

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
ms.openlocfilehash: 4b270c36bdbea9c8d81915eba424cae1054ce7d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008531"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="41692-102">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="41692-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="41692-103">Načte zadanou verzi knihovny DLL, která je součástí .NET Framework Distribuovatelný balíček.</span><span class="sxs-lookup"><span data-stu-id="41692-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="41692-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="41692-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="41692-105">Místo toho použijte metodu [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41692-105">Use the [ICLRRuntimeInfo::LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41692-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41692-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41692-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="41692-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="41692-108">pro Řetězec zakončený nulou, který představuje název knihovny DLL, která má být načtena z knihovny .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41692-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="41692-109">pro Řetězec zakončený nulou, který představuje verzi knihovny DLL, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="41692-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="41692-110">Pokud `szVersion` je null, verze vybraná pro načtení je nejnovější verze zadané knihovny DLL, která je menší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="41692-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="41692-111">To znamená, že všechny verze, které se rovnají nebo jsou vyšší než verze 4, jsou ignorovány `szVersion` , pokud je hodnota null a není-li nainstalována žádná verze, která je nižší než verze 4, knihovna DLL se nepodařilo načíst.</span><span class="sxs-lookup"><span data-stu-id="41692-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="41692-112">K tomu je potřeba zajistit, aby instalace .NET Framework 4 neovlivnila stávající aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="41692-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="41692-113">Podívejte se na záznam [v rámci proc SxS a migrace rychlé zprovoznění](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) na blogu týmu CLR.</span><span class="sxs-lookup"><span data-stu-id="41692-113">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="41692-114">Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="41692-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="41692-115">mimo Ukazatel na popisovač modulu.</span><span class="sxs-lookup"><span data-stu-id="41692-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41692-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="41692-116">Return Value</span></span>  
 <span data-ttu-id="41692-117">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="41692-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="41692-118">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="41692-118">Return code</span></span>|<span data-ttu-id="41692-119">Description</span><span class="sxs-lookup"><span data-stu-id="41692-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="41692-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="41692-120">S_OK</span></span>|<span data-ttu-id="41692-121">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="41692-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="41692-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="41692-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="41692-123">Načítání `szDllName` vyžaduje načtení modulu CLR (Common Language Runtime) a potřebnou verzi modulu CLR nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="41692-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41692-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41692-124">Remarks</span></span>  
 <span data-ttu-id="41692-125">Tato funkce se používá k načtení knihoven DLL, které jsou součástí .NET Framework Distribuovatelný balíček.</span><span class="sxs-lookup"><span data-stu-id="41692-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="41692-126">Nenačítá uživatelem generované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="41692-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41692-127">Počínaje verzí 2,0 .NET Framework, načtení souboru Fusion. dll způsobí načtení modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="41692-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="41692-128">Důvodem je, že funkce v Fusion. dll jsou nyní obálky, jejichž implementace jsou poskytovány modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="41692-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41692-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41692-129">Requirements</span></span>  
 <span data-ttu-id="41692-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41692-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41692-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41692-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41692-132">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41692-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41692-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="41692-133">See also</span></span>

- [<span data-ttu-id="41692-134">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="41692-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

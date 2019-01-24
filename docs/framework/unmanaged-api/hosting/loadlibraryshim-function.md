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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bad6c052ec90c8cd3e47c4ec822fc2d5ae944af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612161"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="15672-102">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="15672-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="15672-103">Načte zadanou verzi knihovny DLL, která je součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15672-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="15672-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15672-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="15672-105">Použití [iclrruntimeinfo::LoadLibrary –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="15672-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15672-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15672-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15672-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="15672-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="15672-108">[in] Ukončit nulou řetězec představující název knihovny DLL, který se má načíst z knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15672-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="15672-109">[in] Ukončit nulou řetězec, který představuje verzi knihovny DLL, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="15672-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="15672-110">Pokud `szVersion` je null, verze vybrali pro načítání je nejnovější verzi určenou knihovnu DLL, která je nižší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="15672-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="15672-111">To znamená, jsou ignorovány všechny verze roven nebo větší než verze 4, pokud `szVersion` má hodnotu null, a pokud je nainstalována žádná verze a menší než verze 4, se nepodaří načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="15672-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="15672-112">Je to z toho k takové instalaci [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nemá vliv na existující aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="15672-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="15672-113">Viz položka [SxS InProc a migrace s rychlým startem](https://go.microsoft.com/fwlink/?LinkId=200329) na blogu týmu CLR.</span><span class="sxs-lookup"><span data-stu-id="15672-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="15672-114">Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="15672-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="15672-115">[out] Ukazatel na popisovač modulu.</span><span class="sxs-lookup"><span data-stu-id="15672-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15672-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="15672-116">Return Value</span></span>  
 <span data-ttu-id="15672-117">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="15672-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="15672-118">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="15672-118">Return code</span></span>|<span data-ttu-id="15672-119">Popis</span><span class="sxs-lookup"><span data-stu-id="15672-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="15672-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="15672-120">S_OK</span></span>|<span data-ttu-id="15672-121">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="15672-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="15672-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="15672-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="15672-123">Načítání `szDllName` vyžaduje načítání common language runtime (CLR) a potřebnou verzi modulu CLR nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="15672-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15672-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15672-124">Remarks</span></span>  
 <span data-ttu-id="15672-125">Tato funkce slouží k načtení knihovny DLL, které jsou součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15672-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="15672-126">Tato možnost nenačte uživatelem generovaný knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="15672-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15672-127">Od verze rozhraní .NET Framework verze 2.0, načítají se soubor Fusion.dll způsobí, že modul CLR, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="15672-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="15672-128">Je to proto, že funkce v soubor Fusion.dll jsou nyní obálky, jehož implementace jsou k dispozici v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="15672-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15672-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15672-129">Requirements</span></span>  
 <span data-ttu-id="15672-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15672-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15672-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15672-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15672-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15672-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15672-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15672-133">See also</span></span>
- [<span data-ttu-id="15672-134">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="15672-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

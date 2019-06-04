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
ms.openlocfilehash: 87ca5470fe5994d34d12a339c2d92a5f3917063d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490220"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="410c5-102">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="410c5-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="410c5-103">Načte zadanou verzi knihovny DLL, která je součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="410c5-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="410c5-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="410c5-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="410c5-105">Použití [iclrruntimeinfo::LoadLibrary –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="410c5-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410c5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="410c5-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="410c5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="410c5-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="410c5-108">[in] Ukončit nulou řetězec představující název knihovny DLL, který se má načíst z knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="410c5-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="410c5-109">[in] Ukončit nulou řetězec, který představuje verzi knihovny DLL, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="410c5-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="410c5-110">Pokud `szVersion` je null, verze vybrali pro načítání je nejnovější verzi určenou knihovnu DLL, která je nižší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="410c5-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="410c5-111">To znamená, jsou ignorovány všechny verze roven nebo větší než verze 4, pokud `szVersion` má hodnotu null, a pokud je nainstalována žádná verze a menší než verze 4, se nepodaří načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="410c5-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="410c5-112">Tím je zajištěno, že instalace rozhraní .NET Framework 4 nemá vliv na existující aplikace nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="410c5-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="410c5-113">Viz položka [SxS InProc a migrace s rychlým startem](https://go.microsoft.com/fwlink/?LinkId=200329) na blogu týmu CLR.</span><span class="sxs-lookup"><span data-stu-id="410c5-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="410c5-114">Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="410c5-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="410c5-115">[out] Ukazatel na popisovač modulu.</span><span class="sxs-lookup"><span data-stu-id="410c5-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="410c5-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="410c5-116">Return Value</span></span>  
 <span data-ttu-id="410c5-117">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="410c5-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="410c5-118">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="410c5-118">Return code</span></span>|<span data-ttu-id="410c5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="410c5-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="410c5-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="410c5-120">S_OK</span></span>|<span data-ttu-id="410c5-121">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="410c5-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="410c5-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="410c5-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="410c5-123">Načítání `szDllName` vyžaduje načítání common language runtime (CLR) a potřebnou verzi modulu CLR nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="410c5-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="410c5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="410c5-124">Remarks</span></span>  
 <span data-ttu-id="410c5-125">Tato funkce slouží k načtení knihovny DLL, které jsou součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="410c5-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="410c5-126">Tato možnost nenačte uživatelem generovaný knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="410c5-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="410c5-127">Od verze rozhraní .NET Framework verze 2.0, načítají se soubor Fusion.dll způsobí, že modul CLR, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="410c5-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="410c5-128">Je to proto, že funkce v soubor Fusion.dll jsou nyní obálky, jehož implementace jsou k dispozici v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="410c5-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410c5-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="410c5-129">Requirements</span></span>  
 <span data-ttu-id="410c5-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410c5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410c5-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="410c5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="410c5-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410c5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410c5-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="410c5-133">See also</span></span>

- [<span data-ttu-id="410c5-134">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="410c5-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

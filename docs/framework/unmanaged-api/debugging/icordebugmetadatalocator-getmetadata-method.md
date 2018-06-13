---
title: ICorDebugMetaDataLocator::GetMetaData – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8c7042f7eee1ccd03d04cc20c5a0db83d986b0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421915"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="05ea7-102">ICorDebugMetaDataLocator::GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="05ea7-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="05ea7-103">Požádá ladicí program na vrátit úplnou cestu k modulu, jehož metadat je potřebný pro dokončení operace, které požadovali ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="05ea7-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ea7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ea7-104">Syntax</span></span>  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05ea7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05ea7-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="05ea7-106">[v] Řetězec ukončené hodnotou null, který představuje úplnou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="05ea7-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="05ea7-107">Pokud je úplná cesta není k dispozici, název a příponu souboru (*filename*. *rozšíření*).</span><span class="sxs-lookup"><span data-stu-id="05ea7-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="05ea7-108">[v] Časové razítko z hlavičky souboru obrázku PE.</span><span class="sxs-lookup"><span data-stu-id="05ea7-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="05ea7-109">Tento parametr může potenciálně použít pro symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="05ea7-109">This parameter can potentially be used for a symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="05ea7-110">[v] Velikost bitové kopie z hlavičky souboru PE.</span><span class="sxs-lookup"><span data-stu-id="05ea7-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="05ea7-111">Tento parametr může potenciálně použít pro vyhledávání SymSrv.</span><span class="sxs-lookup"><span data-stu-id="05ea7-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="05ea7-112">[v] Znak počet za `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="05ea7-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="05ea7-113">[out] Počet `WCHAR`s zapsána do `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="05ea7-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="05ea7-114">Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`s potřebný k uložení cestu.</span><span class="sxs-lookup"><span data-stu-id="05ea7-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="05ea7-115">[out] Ukazatel na vyrovnávací paměť, do kterého bude ladicí program zkopírovat úplnou cestu souboru, který obsahuje požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="05ea7-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="05ea7-116">`ofReadOnly` Příznak z [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu slouží k vyžádání přístup jen pro čtení k metadatům v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="05ea7-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05ea7-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05ea7-117">Return Value</span></span>  
 <span data-ttu-id="05ea7-118">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="05ea7-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="05ea7-119">Všechny ostatní hodnoty HRESULT selhání znamenat, že soubor není dá načíst.</span><span class="sxs-lookup"><span data-stu-id="05ea7-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="05ea7-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05ea7-120">HRESULT</span></span>|<span data-ttu-id="05ea7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="05ea7-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05ea7-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="05ea7-122">S_OK</span></span>|<span data-ttu-id="05ea7-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="05ea7-123">The method completed successfully.</span></span> <span data-ttu-id="05ea7-124">`wszPathBuffer` obsahuje úplnou cestu k souboru a je ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="05ea7-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="05ea7-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="05ea7-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="05ea7-126">Aktuální velikost `wszPathBuffer` není dostatečná pro uložení úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="05ea7-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="05ea7-127">V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`s, včetně ukončující prázdný znak, a `GetMetaData` se nazývá znovu s požadovanou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="05ea7-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ea7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05ea7-128">Remarks</span></span>  
 <span data-ttu-id="05ea7-129">Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpis, určuje cestu z počítače, kde byl shromážděn výpis.</span><span class="sxs-lookup"><span data-stu-id="05ea7-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="05ea7-130">Tento soubor pravděpodobně neexistuje v tomto umístění nebo nesprávný soubor se stejným názvem, můžou být uložené na cestě.</span><span class="sxs-lookup"><span data-stu-id="05ea7-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ea7-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05ea7-131">Requirements</span></span>  
 <span data-ttu-id="05ea7-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ea7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ea7-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05ea7-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05ea7-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05ea7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05ea7-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ea7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ea7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="05ea7-136">See Also</span></span>  
 [<span data-ttu-id="05ea7-137">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ea7-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="05ea7-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="05ea7-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="05ea7-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="05ea7-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

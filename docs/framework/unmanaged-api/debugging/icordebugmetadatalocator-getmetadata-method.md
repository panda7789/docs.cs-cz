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
ms.openlocfilehash: 1149a3c3589cec0e952088a772ca036028c58ff5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521351"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="d9ae7-102">ICorDebugMetaDataLocator::GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="d9ae7-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="d9ae7-103">Dotaz vrátí úplnou cestu k modulu, jehož metadat je potřeba k dokončení operace, které ladicí program požadovaný ladicí program.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ae7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9ae7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d9ae7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9ae7-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="d9ae7-106">[in] Řetězec zakončený hodnotou null, který představuje úplnou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="d9ae7-107">Pokud je úplná cesta není k dispozici, název a příponu souboru (*filename*. *rozšíření*).</span><span class="sxs-lookup"><span data-stu-id="d9ae7-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="d9ae7-108">[in] Časové razítko ze záhlaví PE souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="d9ae7-109">Tento parametr může potenciálně použít pro server symbolů ([SymSrv](https://msdn.microsoft.com/library/cc266470.aspx)) vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-109">This parameter can potentially be used for a symbol server ([SymSrv](https://msdn.microsoft.com/library/cc266470.aspx)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="d9ae7-110">[in] Velikost bitové kopie ze záhlaví PE souboru.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="d9ae7-111">Tento parametr lze použít potenciálně pro vyhledávání SymSrv.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="d9ae7-112">[in] Počet znak za `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="d9ae7-113">[out] Počet `WCHAR`s zapsána do `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="d9ae7-114">Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`s potřebné k uložení této cesty.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="d9ae7-115">[out] Ukazatel do vyrovnávací paměti, do které ladicí program se zkopírovat úplnou cestu souboru, který obsahuje požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="d9ae7-116">`ofReadOnly` Příznak z [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčet slouží k vyžádání přístup jen pro čtení metadat z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9ae7-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9ae7-117">Return Value</span></span>  
 <span data-ttu-id="d9ae7-118">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="d9ae7-119">Všechny ostatní HRESULT – selhání znamenat, že soubor není retrievable.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="d9ae7-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9ae7-120">HRESULT</span></span>|<span data-ttu-id="d9ae7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d9ae7-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9ae7-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9ae7-122">S_OK</span></span>|<span data-ttu-id="d9ae7-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-123">The method completed successfully.</span></span> <span data-ttu-id="d9ae7-124">`wszPathBuffer` obsahuje úplnou cestu k souboru a je zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="d9ae7-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d9ae7-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d9ae7-126">Aktuální velikost `wszPathBuffer` není dostatečná k uložení úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="d9ae7-127">V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`s, včetně ukončujícího znaku null, a `GetMetaData` se volá jednou s velikost požadované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ae7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9ae7-128">Remarks</span></span>  
 <span data-ttu-id="d9ae7-129">Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpis paměti, určuje cestu z počítače, kde byl výpis paměti shromážděn.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="d9ae7-130">Soubor neexistuje na tomto místě nebo nesprávný soubor se stejným názvem, mohou být uloženy v cestě.</span><span class="sxs-lookup"><span data-stu-id="d9ae7-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ae7-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9ae7-131">Requirements</span></span>  
 <span data-ttu-id="d9ae7-132">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ae7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ae7-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9ae7-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9ae7-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9ae7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9ae7-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ae7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ae7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9ae7-136">See Also</span></span>  
 [<span data-ttu-id="d9ae7-137">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9ae7-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="d9ae7-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d9ae7-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d9ae7-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="d9ae7-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

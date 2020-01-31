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
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793054"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="c2ea1-102">ICorDebugMetaDataLocator::GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="c2ea1-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="c2ea1-103">Požádá ladicí program, aby vrátil úplnou cestu k modulu, jehož metadata jsou potřeba k dokončení operace, kterou ladicí program požaduje.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ea1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2ea1-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c2ea1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2ea1-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="c2ea1-106">pro Řetězec zakončený hodnotou null, který představuje úplnou cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="c2ea1-107">Pokud úplná cesta není k dispozici, název a Přípona souboru (*filename*. *rozšíření*).</span><span class="sxs-lookup"><span data-stu-id="c2ea1-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="c2ea1-108">pro Časové razítko z hlaviček souboru v PE bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="c2ea1-109">Tento parametr může být potenciálně použit pro vyhledávání serveru symbolů ([SymSrv](/windows/desktop/debug/using-symsrv)).</span><span class="sxs-lookup"><span data-stu-id="c2ea1-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="c2ea1-110">pro Velikost obrázku z hlavičky souboru PE.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="c2ea1-111">Tento parametr může být potenciálně použit pro SymSrv vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="c2ea1-112">pro Počet znaků v `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="c2ea1-113">mimo Počet `WCHAR`s zapsaných do `wszPathBuffer`</span><span class="sxs-lookup"><span data-stu-id="c2ea1-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="c2ea1-114">Pokud metoda vrátí E_NOT_SUFFICIENT_BUFFER, obsahuje počet `WCHAR`potřebných k uložení cesty.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="c2ea1-115">mimo Ukazatel na vyrovnávací paměť, do které bude ladicí program kopírovat úplnou cestu k souboru, který obsahuje požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="c2ea1-116">Příznak `ofReadOnly` z výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) se používá k vyžádání přístupu k metadatům v tomto souboru jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2ea1-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2ea1-117">Return Value</span></span>  
 <span data-ttu-id="c2ea1-118">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="c2ea1-119">Všechny ostatní chyby HRESULT neznamenají, že soubor nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="c2ea1-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2ea1-120">HRESULT</span></span>|<span data-ttu-id="c2ea1-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c2ea1-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2ea1-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2ea1-122">S_OK</span></span>|<span data-ttu-id="c2ea1-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-123">The method completed successfully.</span></span> <span data-ttu-id="c2ea1-124">`wszPathBuffer` obsahuje úplnou cestu k souboru a je zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="c2ea1-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c2ea1-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c2ea1-126">Aktuální velikost `wszPathBuffer` není dostačující pro uložení úplné cesty.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="c2ea1-127">V takovém případě `pcchPathBuffer` obsahuje potřebný počet `WCHAR`, včetně ukončujícího znaku null a `GetMetaData` je volána podruhé s požadovanou velikostí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2ea1-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2ea1-128">Remarks</span></span>  
 <span data-ttu-id="c2ea1-129">Pokud `wszImagePath` obsahuje úplnou cestu pro modul z výpisu paměti, určuje cestu z počítače, ve kterém byl výpis paměti shromážděn.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="c2ea1-130">Soubor pravděpodobně v tomto umístění neexistuje nebo v cestě je uložen nesprávný soubor se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c2ea1-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ea1-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2ea1-131">Requirements</span></span>  
 <span data-ttu-id="c2ea1-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ea1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ea1-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2ea1-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2ea1-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2ea1-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2ea1-135">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ea1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ea1-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2ea1-136">See also</span></span>

- [<span data-ttu-id="c2ea1-137">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2ea1-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="c2ea1-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c2ea1-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c2ea1-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="c2ea1-139">Debugging</span></span>](index.md)

---
title: IMetaDataImport2::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490401"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="61645-102">IMetaDataImport2::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="61645-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="61645-103">Získá číslo verze modulu runtime, který byl použit k sestavení sestavení.</span><span class="sxs-lookup"><span data-stu-id="61645-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61645-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61645-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61645-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61645-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="61645-106">mimo Pole pro uložení řetězce, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="61645-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="61645-107">pro Velikost pole v různých znacích `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="61645-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="61645-108">mimo V poli se vrátil počet velkých znaků, včetně ukončovacího znaku null `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="61645-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61645-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61645-109">Remarks</span></span>  
 <span data-ttu-id="61645-110">`GetVersionString`Metoda získá vestavěnou verzi aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="61645-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="61645-111">Pokud se obor nikdy neuložil, nebude mít vestavěnou verzi a vrátí se prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="61645-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61645-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61645-112">Requirements</span></span>  
 <span data-ttu-id="61645-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61645-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61645-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="61645-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61645-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="61645-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61645-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61645-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61645-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61645-117">See also</span></span>

- [<span data-ttu-id="61645-118">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61645-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="61645-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61645-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

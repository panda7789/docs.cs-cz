---
title: IMetaDataTables::GetUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501141"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="f4d05-102">IMetaDataTables::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="f4d05-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="f4d05-103">Získá pevně zakódovaný řetězec na zadaném indexu ve sloupci řetězce v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="f4d05-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4d05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4d05-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="f4d05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d05-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="f4d05-106">pro Hodnota indexu, ze které budou načteny pevně zakódovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f4d05-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="f4d05-107">mimo Ukazatel na velikost `ppData` .</span><span class="sxs-lookup"><span data-stu-id="f4d05-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="f4d05-108">mimo Ukazatel na ukazatel na vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="f4d05-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4d05-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4d05-109">Requirements</span></span>

<span data-ttu-id="f4d05-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4d05-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f4d05-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4d05-111">**Header:** Cor.h</span></span>

<span data-ttu-id="f4d05-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f4d05-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="f4d05-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4d05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f4d05-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4d05-114">See also</span></span>

- [<span data-ttu-id="f4d05-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4d05-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f4d05-116">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4d05-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

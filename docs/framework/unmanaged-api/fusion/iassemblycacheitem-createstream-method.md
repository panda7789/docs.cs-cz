---
title: IAssemblyCacheItem::CreateStream – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af7dc4e1694b66fc4a5ce37e515c71e9fa3db49
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796741"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="1a4e0-102">IAssemblyCacheItem::CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="1a4e0-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="1a4e0-103">Vytvoří datový proud se zadaným názvem a formátem.</span><span class="sxs-lookup"><span data-stu-id="1a4e0-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a4e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a4e0-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="1a4e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a4e0-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="1a4e0-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="1a4e0-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="1a4e0-107">pro Název streamu, který se má vytvořit</span><span class="sxs-lookup"><span data-stu-id="1a4e0-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="1a4e0-108">pro Formát souboru, který se má streamovat</span><span class="sxs-lookup"><span data-stu-id="1a4e0-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="1a4e0-109">pro Příznaky specifické pro formát definované v Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="1a4e0-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="1a4e0-110">mimo Ukazatel na adresu vrácené instance [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .</span><span class="sxs-lookup"><span data-stu-id="1a4e0-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="1a4e0-111">[in, volitelné] Maximální velikost datového proudu, na který odkazuje `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="1a4e0-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a4e0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a4e0-112">Requirements</span></span>

<span data-ttu-id="1a4e0-113">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a4e0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1a4e0-114">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1a4e0-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="1a4e0-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1a4e0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a4e0-116">See also</span></span>

- [<span data-ttu-id="1a4e0-117">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a4e0-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)

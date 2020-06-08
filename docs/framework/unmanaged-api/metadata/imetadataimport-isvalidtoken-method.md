---
title: IMetaDataImport::IsValidToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 9190d021b801be951d214406dde7e6d76da15608
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503435"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="f7a54-102">IMetaDataImport::IsValidToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f7a54-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="f7a54-103">Získá hodnotu, která označuje, zda zadaný token drží platný odkaz na objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="f7a54-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7a54-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7a54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7a54-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f7a54-106">pro Token pro kontrolu platnosti odkazu.</span><span class="sxs-lookup"><span data-stu-id="f7a54-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7a54-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7a54-107">Return Value</span></span>  
 <span data-ttu-id="f7a54-108">`true`Pokud `tk` je platný token metadat v rámci aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="f7a54-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="f7a54-109">V opačném případě hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="f7a54-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7a54-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7a54-110">Requirements</span></span>  
 <span data-ttu-id="f7a54-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7a54-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7a54-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7a54-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7a54-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7a54-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7a54-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a54-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7a54-115">See also</span></span>

- [<span data-ttu-id="f7a54-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7a54-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f7a54-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7a54-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

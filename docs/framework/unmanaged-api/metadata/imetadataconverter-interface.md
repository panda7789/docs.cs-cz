---
title: IMetaDataConverter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 7a2a5080872f49a84e36c53ac337d91738c15e45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501336"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="f624e-102">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f624e-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="f624e-103">Poskytuje metody pro mapování knihoven typů na signatury jejich metadat a jejich převod z jednoho na druhý.</span><span class="sxs-lookup"><span data-stu-id="f624e-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f624e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f624e-104">Methods</span></span>  
  
|<span data-ttu-id="f624e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f624e-105">Method</span></span>|<span data-ttu-id="f624e-106">Description</span><span class="sxs-lookup"><span data-stu-id="f624e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f624e-107">GetMetaDataFromTypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="f624e-107">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="f624e-108">Získá ukazatel na instanci [IMetaDataImport](imetadataimport-interface.md) , která představuje signaturu metadat pro knihovnu typů, na kterou odkazuje zadaná `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="f624e-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="f624e-109">GetMetaDataFromTypeLib – metoda</span><span class="sxs-lookup"><span data-stu-id="f624e-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="f624e-110">Získá ukazatel na `IMetaDataImport` instanci, která představuje signaturu metadat pro knihovnu typů reprezentované zadanou `ITypeLib` instancí.</span><span class="sxs-lookup"><span data-stu-id="f624e-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="f624e-111">GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="f624e-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="f624e-112">Získá ukazatel na `ITypeLib` instanci, která představuje knihovnu typů, která má zadaný název modulu a knihovny.</span><span class="sxs-lookup"><span data-stu-id="f624e-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f624e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f624e-113">Requirements</span></span>  
 <span data-ttu-id="f624e-114">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f624e-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f624e-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f624e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f624e-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f624e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f624e-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f624e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f624e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f624e-118">See also</span></span>

- [<span data-ttu-id="f624e-119">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="f624e-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f624e-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f624e-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

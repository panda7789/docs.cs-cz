---
title: IMetaDataImport::GetEventProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9d156d7c7ada8309e501ba44720dfa285ce50d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552356"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="cac7b-102">IMetaDataImport::GetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cac7b-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="cac7b-103">Získá informace metadat pro událost reprezentována token zadané události, včetně deklarující typ, přidat a odebrat metody pro delegáty a všechny příznaky a další související data.</span><span class="sxs-lookup"><span data-stu-id="cac7b-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cac7b-104">Syntax</span></span>  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cac7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cac7b-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="cac7b-106">[in] Událost metadat token reprezentující události se získat metadata pro.</span><span class="sxs-lookup"><span data-stu-id="cac7b-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cac7b-107">[out] Ukazatel na token TypeDef představující třídu, která deklaruje událost.</span><span class="sxs-lookup"><span data-stu-id="cac7b-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="cac7b-108">[out] Název události odkazuje `ev`.</span><span class="sxs-lookup"><span data-stu-id="cac7b-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="cac7b-109">[in] Požadovaná délka širokých znaků `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="cac7b-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="cac7b-110">[out] Vrácená délka v širokých znaků `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="cac7b-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="cac7b-111">[out] Ukazatel Odkaz TypeRef nebo TypeDef metadat token představující <xref:System.Delegate> typ události.</span><span class="sxs-lookup"><span data-stu-id="cac7b-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="cac7b-112">[out] Ukazatel na token metadat reprezentující metodu, která přidá obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cac7b-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="cac7b-113">[out] Ukazatel na token metadat reprezentující metodu, která odebere obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cac7b-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="cac7b-114">[out] Ukazatel na token metadat reprezentující metodu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="cac7b-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="cac7b-115">[out] Pole ukazatelů token jiným metodám přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="cac7b-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cac7b-116">[in] Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="cac7b-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="cac7b-117">[out] Počet tokenů vrátil v `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="cac7b-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac7b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cac7b-118">Requirements</span></span>  
 <span data-ttu-id="cac7b-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cac7b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac7b-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cac7b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cac7b-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cac7b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cac7b-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cac7b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac7b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cac7b-123">See also</span></span>
- [<span data-ttu-id="cac7b-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cac7b-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cac7b-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cac7b-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: "IMetaDataImport::GetEventProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="7ede9-102">IMetaDataImport::GetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7ede9-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="7ede9-103">Získá informace metadat pro událost reprezentována token zadanou událost, včetně deklarující typ, přidat a odebrat metody pro Delegáti a všechny příznaky a další související data.</span><span class="sxs-lookup"><span data-stu-id="7ede9-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ede9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ede9-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="7ede9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ede9-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="7ede9-106">[v] Metadata události token představující události se získat metadata pro.</span><span class="sxs-lookup"><span data-stu-id="7ede9-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="7ede9-107">[out] Ukazatel na TypeDef token představující třídu, který deklaruje události.</span><span class="sxs-lookup"><span data-stu-id="7ede9-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="7ede9-108">[out] Název události odkazuje `ev`.</span><span class="sxs-lookup"><span data-stu-id="7ede9-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="7ede9-109">[v] Požadovaná délka v široké znaky `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="7ede9-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="7ede9-110">[out] Vrácená délka ve znacích široké `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="7ede9-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="7ede9-111">[out] Ukazatel Odkaz TypeRef nebo TypeDef metadata token reprezentující <xref:System.Delegate> typ události.</span><span class="sxs-lookup"><span data-stu-id="7ede9-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="7ede9-112">[out] Ukazatel na metadata token představující metodu, která přidá obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7ede9-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="7ede9-113">[out] Ukazatel na metadata token představující metodu, která odebere obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7ede9-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="7ede9-114">[out] Ukazatel na metadata token představující metodu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="7ede9-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="7ede9-115">[out] Pole tokenu ukazatele na další metody přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="7ede9-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7ede9-116">[v] Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="7ede9-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="7ede9-117">[out] Počet tokeny, vrátí se v `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="7ede9-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ede9-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ede9-118">Requirements</span></span>  
 <span data-ttu-id="7ede9-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ede9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ede9-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7ede9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ede9-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ede9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ede9-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ede9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ede9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ede9-123">See Also</span></span>  
 [<span data-ttu-id="7ede9-124">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ede9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7ede9-125">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ede9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

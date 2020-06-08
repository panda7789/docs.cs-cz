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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491300"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="e3b5f-102">IMetaDataImport::GetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e3b5f-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="e3b5f-103">Získá informace o metadatech události reprezentované zadaným tokenem události, včetně deklarovaného typu, metod přidání a odebrání delegátů a všech příznaků a dalších přidružených dat.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3b5f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e3b5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3b5f-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="e3b5f-106">pro Token metadat události představující událost, pro kterou se mají získat metadata</span><span class="sxs-lookup"><span data-stu-id="e3b5f-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e3b5f-107">mimo Ukazatel na token TypeDef představující třídu, která deklaruje událost.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="e3b5f-108">mimo Název události, na kterou odkazuje `ev` .</span><span class="sxs-lookup"><span data-stu-id="e3b5f-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="e3b5f-109">pro Požadovaná délka v různých znacích `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="e3b5f-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="e3b5f-110">mimo Vrácená délka v různých znacích `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="e3b5f-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="e3b5f-111">mimo Ukazatel na token metadat TypeRef nebo TypeDef představující <xref:System.Delegate> Typ události.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="e3b5f-112">mimo Ukazatel na token metadat představující metodu, která přidává obslužné rutiny pro událost.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="e3b5f-113">mimo Ukazatel na token metadat představující metodu, která odebírá obslužné rutiny pro událost.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="e3b5f-114">mimo Ukazatel na token metadat představující metodu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="e3b5f-115">mimo Pole ukazatelů na tokeny na jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e3b5f-116">pro Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="e3b5f-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="e3b5f-117">mimo Počet tokenů vrácených v `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="e3b5f-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3b5f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3b5f-118">Requirements</span></span>  
 <span data-ttu-id="e3b5f-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3b5f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3b5f-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e3b5f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3b5f-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3b5f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3b5f-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3b5f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b5f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3b5f-123">See also</span></span>

- [<span data-ttu-id="e3b5f-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3b5f-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e3b5f-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3b5f-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

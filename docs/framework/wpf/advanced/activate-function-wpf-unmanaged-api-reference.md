---
title: "Aktivovat funkci (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: Acrivate
api_location: PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68f3f2a29da11a648b8c635667de6493a04ccd54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="107ab-102">Aktivovat funkci (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="107ab-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="107ab-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="107ab-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="107ab-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="107ab-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="107ab-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="107ab-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="107ab-106">Parameters</span></span>  
 <span data-ttu-id="107ab-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="107ab-107">pParameters</span></span>  
 <span data-ttu-id="107ab-108">Ukazatel na okna aktivační parametry.</span><span class="sxs-lookup"><span data-stu-id="107ab-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="107ab-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="107ab-109">ppInner</span></span>  
 <span data-ttu-id="107ab-110">Ukazatel na adresu jedné položce vyrovnávací paměť, která obsahuje odkazy <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="107ab-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107ab-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="107ab-111">Requirements</span></span>  
 <span data-ttu-id="107ab-112">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="107ab-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107ab-113">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="107ab-113">**DLL:**</span></span>  
  
 <span data-ttu-id="107ab-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="107ab-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="107ab-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="107ab-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="107ab-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107ab-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107ab-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="107ab-117">See Also</span></span>  
 [<span data-ttu-id="107ab-118">WPF nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="107ab-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)

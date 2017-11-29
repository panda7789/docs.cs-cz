---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f3c101ad13df9b99a2d872bac8783baed8b4b9a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="getcustomui"></a><span data-ttu-id="60e12-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="60e12-102">GetCustomUI</span></span>
<span data-ttu-id="60e12-103">Voláno rozhraním PresentationHost.exe získat vlastní průběh a chybové zprávy z hostitele, pokud je implementována.</span><span class="sxs-lookup"><span data-stu-id="60e12-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e12-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60e12-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60e12-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60e12-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="60e12-106">[out] Ukazatel na sestavení, které obsahuje zadané hostitele průběh uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60e12-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="60e12-107">[out] Název třídy, která je ideálně uživatelského rozhraní průběhu zadané hostitele [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] soubor s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="60e12-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="60e12-108">Tato třída se nachází v sestavení, která je zadána `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="60e12-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="60e12-109">[out] Ukazatel na sestavení, které obsahuje hostitele zadané chybě uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60e12-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="60e12-110">[out] Název třídy, která je uživatel zadaný hostitele chyby rozhraní, pokud možno soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="60e12-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="60e12-111">Tato třída se nachází v sestavení, která je zadána `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="60e12-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="60e12-112">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60e12-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="60e12-113">HRESULT: ignorovány.</span><span class="sxs-lookup"><span data-stu-id="60e12-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60e12-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60e12-114">Remarks</span></span>  
 <span data-ttu-id="60e12-115">Hostitelskou aplikaci může mít specifické motiv, který nemusí vyhovovat PresentationHost.exe na výchozí uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60e12-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="60e12-116">Pokud je to tento případ, můžete implementovat hostitelskou aplikaci [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) vrátí průběh a chyby uživatelského rozhraní pro PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="60e12-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="60e12-117">PresentationHost.exe bude vždy volat [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) před použitím jeho výchozí uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60e12-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="60e12-118">Tato funkce je volána jednou během inicializace PresentationHost společnosti.</span><span class="sxs-lookup"><span data-stu-id="60e12-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e12-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="60e12-119">See Also</span></span>  
 [<span data-ttu-id="60e12-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="60e12-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)

---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: af51a0d76ac080017f58ac8fc3acca86c23fb480
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474862"
---
# <a name="getcustomui"></a><span data-ttu-id="052d2-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="052d2-102">GetCustomUI</span></span>
<span data-ttu-id="052d2-103">Voláno rozhraním PresentationHost.exe získat vlastní pokrok a chybové zprávy z hostitele, pokud implementovaná.</span><span class="sxs-lookup"><span data-stu-id="052d2-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="052d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="052d2-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="052d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="052d2-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="052d2-106">[out] Ukazatel, který obsahuje uživatelské rozhraní poskytované hostitele průběh sestavení.</span><span class="sxs-lookup"><span data-stu-id="052d2-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="052d2-107">[out] Název třídy, který je zadán hostitel průběh uživatelského rozhraní, ideálně [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] soubor s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="052d2-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="052d2-108">Tato třída se nachází v sestavení, která je zadána `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="052d2-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="052d2-109">[out] Ukazatel na sestavení, která obsahuje hostitele zadanou chybovou uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="052d2-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="052d2-110">[out] Název třídy, který je zadán hostitel chyba uživatele pokud možno rozhraní soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="052d2-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="052d2-111">Tato třída se nachází v sestavení, která je zadána `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="052d2-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="052d2-112">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="052d2-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="052d2-113">HODNOTA HRESULT: Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="052d2-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="052d2-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="052d2-114">Remarks</span></span>  
 <span data-ttu-id="052d2-115">Hostitelská aplikace může mít konkrétní motivu, který nemusí vyhovovat vaší PresentationHost.exe výchozí uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="052d2-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="052d2-116">Pokud je to tento případ, můžete implementovat hostitelskou aplikaci [GetCustomUI –](getcustomui.md) vrátit průběh a Chyba uživatelského rozhraní pro PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="052d2-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="052d2-117">Vždy zavolá PresentationHost.exe [GetCustomUI –](getcustomui.md) před použitím jeho výchozí uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="052d2-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="052d2-118">Tato funkce je volána jednou během inicializace PresentationHost společnosti.</span><span class="sxs-lookup"><span data-stu-id="052d2-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052d2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="052d2-119">See also</span></span>
- [<span data-ttu-id="052d2-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="052d2-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)

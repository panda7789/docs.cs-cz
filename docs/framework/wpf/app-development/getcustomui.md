---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005708"
---
# <a name="getcustomui"></a><span data-ttu-id="557b4-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="557b4-102">GetCustomUI</span></span>
<span data-ttu-id="557b4-103">Volá se nástrojem PresentationHost. exe, aby se získaly vlastní průběh a chybové zprávy z hostitele, pokud je implementovaná.</span><span class="sxs-lookup"><span data-stu-id="557b4-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="557b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="557b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="557b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="557b4-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="557b4-106">mimo Ukazatel na sestavení, které obsahuje uživatelské rozhraní průběhu zadané hostitelem.</span><span class="sxs-lookup"><span data-stu-id="557b4-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="557b4-107">mimo Název třídy, která je uživatelské rozhraní průběhu dodané hostitelem, nejlépe je soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="557b4-107">[out] The name of the class that is the host-supplied progress user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="557b4-108">Tato třída se nachází v sestavení určeném parametrem `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="557b4-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="557b4-109">mimo Ukazatel na sestavení, které obsahuje uživatelské rozhraní chyby zadané hostitelem.</span><span class="sxs-lookup"><span data-stu-id="557b4-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="557b4-110">mimo Název třídy, která je uživatelem poskytnutá chyba uživatelského rozhraní, nejlépe je soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="557b4-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="557b4-111">Tato třída se nachází v sestavení určeném parametrem `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="557b4-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="557b4-112">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="557b4-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="557b4-113">HRESULT: ignorováno.</span><span class="sxs-lookup"><span data-stu-id="557b4-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="557b4-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="557b4-114">Remarks</span></span>  
 <span data-ttu-id="557b4-115">Hostitelská aplikace může mít konkrétní motiv, který nemusí splňovat výchozí uživatelská rozhraní PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="557b4-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="557b4-116">Pokud se jedná o tento případ, hostitelská aplikace může implementovat [GetCustomUI](getcustomui.md) a vrátit tak průběh a chybná uživatelská rozhraní PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="557b4-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="557b4-117">PresentationHost. exe bude před použitím výchozích uživatelských rozhraní vždy volat [GetCustomUI](getcustomui.md) .</span><span class="sxs-lookup"><span data-stu-id="557b4-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="557b4-118">Tato funkce se volá jednou během inicializace PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="557b4-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="557b4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="557b4-119">See also</span></span>

- [<span data-ttu-id="557b4-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="557b4-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)

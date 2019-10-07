---
ms.openlocfilehash: 4d67da34cf692133df95480a7f0215943337a34e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003025"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="afa8d-101">Odebrala se duplicitní rozhraní API z model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="afa8d-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="afa8d-102">Počet rozhraní API náhodně duplicitních duplikován v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který začíná v rozhraní .NET Core 3,0 Preview 4, byl v rozhraní .NET Core 3,0 RC1 odebraný.</span><span class="sxs-lookup"><span data-stu-id="afa8d-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="afa8d-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="afa8d-103">Change description</span></span>

<span data-ttu-id="afa8d-104">.NET Core 3,0 Preview 4 neúmyslně duplikoval určitý počet typů v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který již existoval v oboru názvů <xref:System.ComponentModel.Design?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="afa8d-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="afa8d-105">Od verze .NET Core 3,0 RC1 tyto duplicitní typy již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="afa8d-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="afa8d-106">V následující tabulce je uveden původní typ a jeho duplicitní typ:</span><span class="sxs-lookup"><span data-stu-id="afa8d-106">The following table shows lists the original type and its duplicated type:</span></span>

|<span data-ttu-id="afa8d-107">Původní typ</span><span class="sxs-lookup"><span data-stu-id="afa8d-107">Original type</span></span>|<span data-ttu-id="afa8d-108">Duplicitní typ</span><span class="sxs-lookup"><span data-stu-id="afa8d-108">Duplicated type</span></span>|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="afa8d-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="afa8d-109">Version introduced</span></span>

<span data-ttu-id="afa8d-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="afa8d-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="afa8d-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="afa8d-111">Recommended action</span></span>

<span data-ttu-id="afa8d-112">Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **původní typ** tabulky.</span><span class="sxs-lookup"><span data-stu-id="afa8d-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="afa8d-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="afa8d-113">Category</span></span>

<span data-ttu-id="afa8d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afa8d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="afa8d-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="afa8d-115">Affected APIs</span></span>

- <span data-ttu-id="afa8d-116">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="afa8d-116">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

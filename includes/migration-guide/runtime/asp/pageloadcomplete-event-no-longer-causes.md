---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619930"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="f1d96-101">Událost Page. LoadComplete již nezpůsobí, že ovládací prvek System. Web. UI. WebControls. EntityDataSource vyvolá datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="f1d96-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="f1d96-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f1d96-102">Details</span></span>

<span data-ttu-id="f1d96-103"><xref:System.Web.UI.Page.LoadComplete>Událost již nezpůsobuje, <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> aby ovládací prvek vyvolal datovou vazbu pro změny v parametrech Create, Update a DELETE.</span><span class="sxs-lookup"><span data-stu-id="f1d96-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="f1d96-104">Tato změna eliminuje nadbytečné cesty k databázi, zabraňuje resetu hodnot ovládacích prvků a vytváří chování, které je konzistentní s jinými ovládacími prvky dat, jako jsou <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> a <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="f1d96-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="f1d96-105">Tato změna vytváří různé chování v nepravděpodobném případě, že aplikace spoléhají na vyvolání datových vazeb v <xref:System.Web.UI.Page.LoadComplete> události.</span><span class="sxs-lookup"><span data-stu-id="f1d96-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f1d96-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="f1d96-106">Suggestion</span></span>

<span data-ttu-id="f1d96-107">Pokud je potřeba vytvořit datovou vazbu, ručně Vyvolejte příkaz DataBind v události, která je výše v příspěvku po návratu.</span><span class="sxs-lookup"><span data-stu-id="f1d96-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="f1d96-108">Name</span><span class="sxs-lookup"><span data-stu-id="f1d96-108">Name</span></span>    | <span data-ttu-id="f1d96-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f1d96-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f1d96-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f1d96-110">Scope</span></span>   |<span data-ttu-id="f1d96-111">Edge</span><span class="sxs-lookup"><span data-stu-id="f1d96-111">Edge</span></span>|
|<span data-ttu-id="f1d96-112">Verze</span><span class="sxs-lookup"><span data-stu-id="f1d96-112">Version</span></span>|<span data-ttu-id="f1d96-113">4.5</span><span class="sxs-lookup"><span data-stu-id="f1d96-113">4.5</span></span>|
|<span data-ttu-id="f1d96-114">Typ</span><span class="sxs-lookup"><span data-stu-id="f1d96-114">Type</span></span>|<span data-ttu-id="f1d96-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f1d96-115">Runtime</span></span>|

---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619930"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Událost Page. LoadComplete již nezpůsobí, že ovládací prvek System. Web. UI. WebControls. EntityDataSource vyvolá datovou vazbu.

#### <a name="details"></a>Podrobnosti

<xref:System.Web.UI.Page.LoadComplete>Událost již nezpůsobuje, <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> aby ovládací prvek vyvolal datovou vazbu pro změny v parametrech Create, Update a DELETE. Tato změna eliminuje nadbytečné cesty k databázi, zabraňuje resetu hodnot ovládacích prvků a vytváří chování, které je konzistentní s jinými ovládacími prvky dat, jako jsou <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> a <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName> . Tato změna vytváří různé chování v nepravděpodobném případě, že aplikace spoléhají na vyvolání datových vazeb v <xref:System.Web.UI.Page.LoadComplete> události.

#### <a name="suggestion"></a>Návrh

Pokud je potřeba vytvořit datovou vazbu, ručně Vyvolejte příkaz DataBind v události, která je výše v příspěvku po návratu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|

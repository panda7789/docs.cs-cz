---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616042"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="64b11-101">DataObject. GetData teď načítá data jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="64b11-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="64b11-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64b11-102">Details</span></span>

<span data-ttu-id="64b11-103">Pro aplikace cílené na .NET Framework 4 nebo spuštěné v .NET Framework 4.5.1 nebo dřívějších verzích `DataObject.GetData` načte data ve formátu HTML jako řetězec ASCII.</span><span class="sxs-lookup"><span data-stu-id="64b11-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="64b11-104">V důsledku toho jsou znaky, které nejsou ASCII (znaky, jejichž kódy ASCII jsou větší než 0x7F), reprezentovány dvěma náhodnými znaky.</span><span class="sxs-lookup"><span data-stu-id="64b11-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="64b11-105">U aplikací, které cílí na .NET Framework 4,5 nebo novější, a jejich spuštění v .NET Framework 4.5.2 `DataObject.GetData` načte data ve formátu HTML jako UTF-8, která představuje znaky větší než 0x7F správně.</span><span class="sxs-lookup"><span data-stu-id="64b11-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="64b11-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="64b11-106">Suggestion</span></span>

<span data-ttu-id="64b11-107">Pokud jste implementovali alternativní řešení potíží s kódováním pomocí řetězců ve formátu HTML (například explicitním kódováním řetězce HTML načteného ze schránky předáním do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) a změnou cílení aplikace z verze 4 na 4,5, mělo by se toto alternativní řešení odebrat. Pokud z nějakého důvodu dojde k původnímu chování, aplikace může cílit na .NET Framework 4,0, aby se toto chování dostalo.</span><span class="sxs-lookup"><span data-stu-id="64b11-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="64b11-108">Name</span><span class="sxs-lookup"><span data-stu-id="64b11-108">Name</span></span>    | <span data-ttu-id="64b11-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="64b11-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="64b11-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="64b11-110">Scope</span></span>   | <span data-ttu-id="64b11-111">Edge</span><span class="sxs-lookup"><span data-stu-id="64b11-111">Edge</span></span>        |
| <span data-ttu-id="64b11-112">Verze</span><span class="sxs-lookup"><span data-stu-id="64b11-112">Version</span></span> | <span data-ttu-id="64b11-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="64b11-113">4.5.2</span></span>       |
| <span data-ttu-id="64b11-114">Typ</span><span class="sxs-lookup"><span data-stu-id="64b11-114">Type</span></span>    | <span data-ttu-id="64b11-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="64b11-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="64b11-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64b11-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
